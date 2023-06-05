# Reproduction for [issue WEB-61348](https://youtrack.jetbrains.com/issue/WEB-61348)

## Steps to reproduce

1. Open the project in PhpStorm (or WebStorm)
2. Run `pnpm i` in the terminal (tested with pnpm 8.6.0)
3. Open `packages/A/a.test.ts` and run the test
   - The test should pass
4. Open `packages/B/b.test.ts` and run the test
   - The test should pass but fails with error (note incorrect `@jest/transform` version):

   ```
     ● Test suite failed to run

    TypeError: Jest: a transform must export a `process` function.

      at ScriptTransformer._getTransformer (../../node_modules/.pnpm/@jest+transform@26.6.2/node_modules/@jest/transform/build/ScriptTransformer.js:360:13)
    ```
5. Note that all these commands work as expected with passing tests (for me):
    - `cd packages/B && pnpm test`
    - `cd packages/B && pnpm jest`
    - `cd packages/B && node node_modules/jest/bin/jest.js`


## Environment

Tested with:

- PhpStorm PhpStorm 2023.1.2, Build #PS-231.9011.38, built on May 16, 2023
- pnpm 8.6.0
- Node.js v18.15.0
- MacOS 13.4
