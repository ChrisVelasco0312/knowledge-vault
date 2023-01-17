### Start a project
Run the command `npm create vite@latest` and follow the prompts
more info [in this guide](https://vitejs.dev/guide/)

### Setting up eslint
1. **Dependencies
`npm install eslint prettier @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-prettier eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react`
-   [ESLint](https://github.com/eslint/eslint): Our main linter.
-   [Prettier](https://github.com/prettier/prettier): Our main code formatter.
-   [@typescript-eslint/eslint-plugin](https://github.com/typescript-eslint/typescript-eslint/tree/main/packages/eslint-plugin): An ESLint plugin which provides rules for TypeScript codebases.
-   [@typescript-eslint/parser](https://github.com/typescript-eslint/typescript-eslint/tree/main/packages/parser): A parser which allows ESLint to lint TypeScript source code.
-   [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier): An ESLint configuration which disables the formatting rules in ESLint that Prettier is going to be responsible for handling, hence avoiding any clashes.
-   [eslint-plugin-import](https://github.com/import-js/eslint-plugin-import): Tells ESLint how to resolve imports.
-   [eslint-plugin-jsx-a11y](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y): Checks for accessiblity issues.
-   [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react): React specific linting rules for ESLint.

2. **Configure eslint**
	Create a `.eslintrc.js` 
	
```js
module.exports = {
  extends: [
    // By extending from a plugin config, we can get recommended rules without having to add them manually.
    'eslint:recommended',
    'plugin:react/recommended',
    'plugin:import/recommended',
    'plugin:jsx-a11y/recommended',
    'plugin:@typescript-eslint/recommended',
    // This disables the formatting rules in ESLint that Prettier is going to be responsible for handling.
    // Make sure it's always the last config, so it gets the chance to override other configs.
    'eslint-config-prettier',
  ],
  settings: {
    react: {
      // Tells eslint-plugin-react to automatically detect the version of React to use.
      version: 'detect',
    },
    // Tells eslint how to resolve imports
    'import/resolver': {
      node: {
        paths: ['src'],
        extensions: ['.js', '.jsx', '.ts', '.tsx'],
      },
    },
  },
  rules: {
    // disable import react 
    'react/react-in-jsx-scope': 'off',
  },
};
```

3. **ESlint ignore file**
Create an `.eslintignore`
```
node_modules/
dist/
.prettierrc.js
.eslintrc.js
env.d.ts
```
4. **Add new sccript entry**
In `package.json` add:
```json
  "scripts": {
    ...
    "lint": "eslint . --ext .ts,.tsx"
  },
```
Run `npm run lint`


