# Configuring Eslint Linter and Prettier for React App

This document describe the needed steps to add Eslint and Prettier to an existing `Create-React-App`.

## VsCode plug-ins

In the Extension tabs of VsCode install the following plug-ins:

- Eslint
- Prettier

## Libraries

Install the following packaes:

```yarn
yarn add eslint-config-airbnb eslint-config-prettier eslint-plugin-html eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks prettier
```

## Configuration

- Add a file `.eslintrc.js` in the root folder of the project with the following:

```js
module.exports = {
    "extends": [
      "airbnb",
      "prettier",
      "prettier/react"
    ],
    "parser": "babel-eslint",
    "parserOptions": {
      "ecmaVersion": 2018,
      "ecmaFeatures": {
        "impliedStrict": true,
        "classes": true
      }
    },
    "env": {
      "browser": true,
      "node": true,
      "jquery": true,
      "jest": true
    },
    "rules": {
      "no-debugger": 0,
      "no-alert": 0,
      "no-await-in-loop": 0,
      "no-return-assign": [
        "error",
        "except-parens"
      ],
      "no-restricted-syntax": [
        2,
        "ForInStatement",
        "LabeledStatement",
        "WithStatement"
      ],
      "no-unused-vars": [
        1,
        {
          "ignoreSiblings": true,
          "argsIgnorePattern": "res|next|^err"
        }
      ],
      "prefer-const": [
        "error",
        {
          "destructuring": "all",
        }
      ],
      "arrow-body-style": [
        2,
        "as-needed"
      ],
      "no-unused-expressions": [
        2,
        {
          "allowTaggedTemplates": true
        }
      ],
      "no-param-reassign": [
        2,
        {
          "props": false
        }
      ],
      "import/no-extraneous-dependencies": [
        "error", {"devDependencies": true}
      ],
      "no-plusplus":0,
      "no-console": 0,
      "import/prefer-default-export": 0,
      "import": 0,
      "func-names": 0,
      "space-before-function-paren": 0,
      "comma-dangle": 0,
      "max-len": 0,
      "import/extensions": 0,
      "no-underscore-dangle": 0,
      "consistent-return": 0,
      "react/display-name": 1,
      "react/no-array-index-key": 0,
      "react/react-in-jsx-scope": 0,
      "react/prefer-stateless-function": 0,
      "react/forbid-prop-types": 0,
      "react/no-unescaped-entities": 0,
      "jsx-a11y/accessible-emoji": 0,
      "react/require-default-props": 0,
      "react/jsx-filename-extension": [
        1,
        {
          "extensions": [
            ".js",
            ".jsx"
          ]
        }
      ],
      "radix": 0,
      "no-shadow": [
        2,
        {
          "hoist": "all",
          "allow": [
            "resolve",
            "reject",
            "done",
            "next",
            "err",
            "error"
          ]
        }
      ],
      "quotes": [
        2,
        "single",
        {
          "avoidEscape": true,
          "allowTemplateLiterals": true
        }
      ],
      "prettier/prettier": [
        "error",
        {
          "trailingComma": "es5",
          "singleQuote": true,
          "printWidth": 80,
        }
      ],
      "jsx-a11y/href-no-hash": "off",
      "jsx-a11y/anchor-is-valid": [
        "warn",
        {
          "aspects": [
            "invalidHref"
          ]
        }
      ],
      "react-hooks/rules-of-hooks": "error",
      "react-hooks/exhaustive-deps": "warn"
    },
    "plugins": [
      "html",
      "prettier",
      "react-hooks"
    ]
  }
```

- Add a file `.eslintignore` in the root folder of the project with the following:

```text
build/*
public/*
src/react-app-env.d.ts
src/serviceWorker.ts
```

- Add the following commands in `package.json`:

```js
{
    ...
    "scripts": {
        ...
        "lint": "yarn eslint --ext .js,.jsx,.ts,.tsx src",
        "lint-fix": "yarn eslint --ext .js,.jsx,.ts,.tsx src --fix"
    },
    ...
}
```

- Edit your local project vsCode Editor configuration as follow:

  - Create `.vscode` folder in the root folder.
  - Create the file `./vscode/settings.json`.
  - Add the following configuration:

  ```js
    {
        // auto-save configs
        "editor.formatOnSave": true,

        // default line ending
        "files.eol": "\n"

        // turn it off for JS and JSX, we will do this via eslint
        "[javascript]": {
            "editor.formatOnSave": false
        },
        "[javascriptreact]": {
            "editor.formatOnSave": false
        },

        // tell the ESLint plugin to run on save
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true
        },

        // Optional BUT IMPORTANT: If you have the prettier extension enabled for other languages like CSS and HTML, turn it off for JS since we are doing it through Eslint already
        "prettier.disableLanguages": [
            "javascript",
            "javascriptreact"
        ],
    }
  ```
