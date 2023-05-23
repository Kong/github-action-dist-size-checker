# github-action-dist-size-checker

# Summary

- compare size if the `dist/` folder (excluding source map files), which the error and warning limits defined in `package.json`. If dist/ size is bigger - show error and cancel workflow or show warning.
- works with mono-repositories (require each project's package.json to define its own limits)

## usage

- in package.json define following object:

```json
"distSizeChecker": {
    "distFolder": "dist/",
    "warningLimit": "22 MB",
    "errorLimit": "25 MB"
}
```
where
||  |
| -------- | ------- |
**distFolder** | relative path to folder where assets are build (default `dist/`)
**warningLimit**| when size of assets in the `distFolder` exceeds this limit - github warning is produced. When this property is not specified, warning is producded when dist dist/ size greater of equal 90% for errorLimit
**errorLimit**| when size of assets in the `distFolder` exceeds this limit - github error is produced

Both `errorLimit` and `warningLimit` needs to be specified in megabytes `MB` or kilobytes `KB`.

- in your yaml wworkflow , after the build step

```yaml
    - name: Check the bundle sizes
      uses: Kong/github-action-dist-size-checker@main
```

## Warning example

## Error example
