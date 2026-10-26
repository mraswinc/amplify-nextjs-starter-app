## AWS Amplify + Next.js starter

This is a starter application for building fullstack apps with AWS Amplify. 

Learn more: https://docs.amplify.aws/gen2/start/quickstart/ 

### Getting Started

This project requires Node.js 22 (LTS) or later. Verify your version:

```bash
node --version
```

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

### Pinned dependency versions

- `typescript` is held on the `5.x` line. TypeScript 7.0 was tested and is not usable yet:
  `typescript-eslint` (bundled by `eslint-config-next` 16) aborts with
  "typescript-eslint does not support TS 7.0", and TS 7 removed `target: ES5`, which
  `tsconfig.json` relies on (`error TS5108`), so `tsc --noEmit`, `next build`'s type check,
  and `eslint .` all fail. Revisit once `typescript-eslint` supports TS 7.
- `@types/node` is held on the `22.x` line deliberately, to match the Node.js 22 runtime
  declared in `.nvmrc` and `package.json` `engines`.

### Known residual `npm audit` advisories

`npm audit` reports high-severity advisories that cannot currently be resolved in this
repository:

- `@graphql-tools/utils` (prototype pollution in `mergeDeep`), reached via
  `@aws-amplify/graphql-generator` -> `@aws-amplify/backend-data` -> `@aws-amplify/backend`.
  npm reports "No fix available".
- `zod`, reached via `@aws-blocks/hosting`.
- `@aws-amplify/platform-core`, reached via `@aws-amplify/schema-generator`.

Justification for accepting them:

- They come from the latest published `@aws-amplify/backend` / `@aws-amplify/backend-cli`
  versions; no upgrade or `npm audit fix` resolves them today.
- They are `devDependencies` used only by the Amplify CLI at build/deploy time and are not
  included in the Next.js production bundle served to users.
- Direct dependencies that could be remediated are already constrained via the `overrides`
  block in `package.json`.

Re-run `npm audit fix` once AWS Amplify publishes releases depending on patched versions.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
