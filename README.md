# esbuild-test

To repro:

1. run `yarn && bazel build :bundle`
2. open `bazel-bin/module-1/bundle.js`
3. notice that only one copy of `stylis.js` actually gets bundled — the one at `node_modules/stylis/stylis.js` (can cmd-f for "stylis.js")

You can compare this to the output of `npx esbuild module-1/index.ts --bundle --platform=node > test-bundle.js`. If you run both files, you'll see something like the following:

```
node test-bundle.js
> [Function: stylis2] { use: [Function: use], set: [Function: set] }
> css-1r0846s
```

```
node bazel-bin/module-1/bundle.js
> ...
> TypeError: stylis.middleware is not a function
> ...
```
