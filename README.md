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
