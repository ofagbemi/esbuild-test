# esbuild-test

To repro:

1. run `yarn && bazel build :bundle`
2. open `bazel-bin/module-1/bundle.js`
3. notice that only one copy of `stylis.js` actually gets bundled — the one at `node_modules/stylis/stylis.js` (can cmd-f for "stylis.js")
