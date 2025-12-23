# Prettier configuration

[Prettier](https://prettier.io/) is an opinionated formatter, which can be [partially configured](https://prettier.io/docs/configuration#editorconfig) using [`.editorconfig`](https://editorconfig.org/). Remaining settings, which can not be configured via `.editorconfig` are left up to Prettier defaults [in line with it's philosophy](https://prettier.io/docs/why-prettier#building-and-enforcing-a-style-guide).

## Setup guide

1. Install `prettier` as a dev dependency (`pnpm add -D prettier`) and copy the following file as `.editorconfig` to the **root** of your project:

```
root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
max_line_length = 120
indent_style = space
indent_size = 4

[{*.yml,*.yaml}]
indent_size = 2
```

2. Add following scripts to your `package.json` file:

```json
    "scripts": {
        "format:check": "prettier --cache --ignore-unknown --check .",
        "format:fix": "prettier --cache --ignore-unknown --write --log-level warn ."
    },
```

**Note:** In case you don't have `.gitignore` file in the directory where you installed `prettier` you should add it using the [`--ignore-path`](https://prettier.io/docs/cli#--ignore-path) option. You'll also need to specify the path to `.prettierignore` as well.

```json
    "scripts": {
        "format:run": "prettier --ignore-unknown --ignore-path=.prettierignore --ignore-path=../../.gitignore",
        "format:check": "pnpm run format:run --cache --check .",
        "format:fix": "pnpm run format:run --log-level warn --cache --write .",
    }
```

3. Create an `.prettierignore` file with the following content:

```
#####################################################
### .prettierignore (https://prettier.io/docs/ignore)
#####################################################

# Ignore all package manager files
yarn*
.yarn/*
.pnp.*
.npmrc
package-lock.json
pnpm-lock.yaml

# Ignore all files specifically marked as ignorable
.*ignore

```