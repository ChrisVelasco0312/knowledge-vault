## Setup a project for typescript

- Create a folder for the project and then start Node.js and package.json
`npm init -y`
- Add typescript as dev dependency
`npm i typescript --save-dev`
- Install ambient Node.js types for TypeScript:
`npm install @types/node --save-dev`
- Create a tsconfig.json
The file where we define the TypeScript compiler options.
```bash
npx tsc --init --rootDir src --outDir build \
--esModuleInterop --resolveJsonModule --lib es6 \
--module commonjs --allowJs true --noImplicitAny true
```
##### explanation
-   `rootDir`: This is where TypeScript looks for our code. We've configured it to look in the `src/` folder. That's where we'll write our TypeScript.
-   `outDir`: Where TypeScript puts our compiled code. We want it to go to a `build/` folder.
-   `esModuleInterop`: If you were in the JavaScript space over the past couple of years, you might have recognized that modules systems had gotten a little bit out of control (AMD, SystemJS, ES Modules, etc). For a topic that requires a much longer discussion, if we're using `commonjs` as our module system (for Node apps, you should be), then we need this to be set to `true`.
-   `resolveJsonModule`: If we use JSON in this project, this option allows TypeScript to use it.
-   `lib`: This option adds _ambient_ types to our project, allowing us to rely on features from different Ecmascript versions, testing libraries, and even the browser DOM api. We'd like to utilize some `es6` language features. This all gets compiled down to `es5`.
-   `module`: `commonjs` is the standard Node module system in 2019. Let's use that.
-   `allowJs`: If you're converting an old JavaScript project to TypeScript, this option will allow you to include `.js` files among `.ts` ones.
-   `noImplicitAny`: In TypeScript files, don't allow a type to be unexplicitly specified. Every type needs to either have a specific type or be explicitly declared `any`. No implicit `any`s.


- Create the src folder an create the first TypeScript file
`mkdir src`
`touch src/index.ts`
write some code
- Compile typescript
`npm tsc`

##### Useful configurations and scripts
- **Cold reloading**: `npm install --save-dev ts-node nodemon`
- Add nodemon.json config:
```json
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "npx ts-node ./src/index.ts"
}
```
`"start:dev": "npx nodemon"`
##### Creating productions builds
- Install `rimraf` , a cross-platform tool that acts lke `rm -rf`
	`npm i --save-dev rim-raf`
 - Add the script
	 `"build": "rimraf ./build & tsc`
When we run build,. rimraf will remove our old build folder before the TypeScript compiler emits new code to `dist`
#### Production startup script
To start the app in production, we need to run the `build` command first, Then execute the compiled JavaScript
`"start":"npm run build && node build/index.js`

# Setup EsLint

#### Instalation and setup

```bash
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

`touch .eslintrc`
```json
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ]
}
```

##### Ignore files
Create `.eslintignore`
```
node_modules
dist
```

##### Adding a lint script