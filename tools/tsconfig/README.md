# TypeScript configuration

Shared TypeScript configurations package for the monorepo.

> [!IMPORTANT]
> The configuration requires TypeScript >= 5.4
> Make sure that your project uses sufficient TypeScript version.

> [!NOTE]
> This configuration is based on [@total-typescript/tsconfig](https://github.com/total-typescript/tsconfig), which provides sensible defaults for modern TypeScript development, with customizations tailored for this project's needs.

## Usage

1. Install [`typescript`](https://www.npmjs.com/package/typescript) and `@tt/typescript-config` as a `dev` dependency (if not already installed).

```shell
pnpm add --save-dev typescript "@tt/typescript-config@workspace:^"
```

2. Create a `tsconfig.json` configuration in your project based on the templates below:
    - [React Application](#react-application)

3. Add the following script to your `package.json` file:

```json
    "scripts": {
        "types:check": "tsc --noEmit"
    }
```

### React Application

For React applications using a bundler (Vite, Webpack, etc.).

_/apps/admin-fe/tsconfig.json_

```json
{
    "extends": ["@tt/typescript-config/react"],
    "include": ["src/**/*", "*.ts", "*.mts"],
    "compilerOptions": {
        /* Paths specification */
        "baseUrl": ".",
        "outDir": "./dist",
        "paths": {
            "@/*": ["./src/*"]
        }
    }
}
```
