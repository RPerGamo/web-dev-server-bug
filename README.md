# Example workspaces project for demoing Web Dev Server 0.4 bug with circular references in workspaces

Steps to reproduce:

1. Clone the project
2. Install dependencies with NPM
3. "npm run start" in "packages/comp-c"

`comp-a` has a dependency to `comp-b`, `comp-b` has a dependency to `comp-c`, and `comp-c` has a dev dependency to `comp-a`.

With `@web/dev-server` 0.4 (latest version), an error occurs: "Error while handling server request". It does not resolve imports correctly.

With versions 0.3 or lower, there is no error; circular references are correctly resolved. You can test it setting `^0.3.0` version for dev server in root package json and reinstalling dependencies.