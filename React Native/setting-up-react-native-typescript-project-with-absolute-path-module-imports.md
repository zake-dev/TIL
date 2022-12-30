# Setting Up React Native Typescript Project with Absolute Path Module Imports

This article is only for who created React Native project with `React Native CLI` and `TypeScript`.

## 1. Install `babel-plugin-module-resolver`

`babel-plugin-module-resolver` is a plugin that allows you to use alias of relative paths based on root directory. The latest version of the plugin is `4.1.0` but it raises vulnerability errors over `>= 2.3.0` version. Ignore that warning. If you try to run `npm audit fix --force` to solve it, the project build will be failed due to it.

## 2. Setting Up `babel.config.js` and `tsconfig.json`

### `babel.config.js`

Add code below at the end of `babel.config.js`. Set `root` as your `src` folder path, and put aliases whatever you want. You have to wrap with `[]` if the real path of the alias indicates outside of `src` folder like root directory.

```javascript
module.exports = {
  ...
  plugins: [
    [
      "module-resolver",
      {
        root: ["./src"],
        extensions: [".ios.js", ".android.js", ".js", ".ts", ".tsx", ".json"],
        alias: {
          "@": "./src",
          "@assets": ["./assets/"],
          "@tests": ["./tests/"],
          "@components": "./src/components",
        },
      },
    ],
  ],
};
```

### `tsconfig.json`

As same way as above, you should write paths on `tsconfig.json` as well. After you put paths on the file, VSCode will allow you to import modules automatically with aliases. Be careful that the syntax of aliases in `tsconfig.json` is slightly different to `babel.config.js`.

```json
{
  ...
  "include": ["./App.tsx", "./src/**/*", "./assets/**/*", "tests/**/*"],
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"],
      "@assets/*": ["assets/*"],
      "@tests/*": ["tests/*"],
      "@components/*": ["src/components/*"],
    }
  }
  ...
}
```

## 3. Reset React Native Cache

After all, you must reset the cache of react native build. If not, the compiler will show errors that it cannot find some modules.

Type `npx react-native start --reset-cache` on terminal.

## 4. Conclusion

That's all! Now you can import modules with absolute path like below!

```typescript
// Before
import RegisterButton from "../../Buttons/RegisterButton";
import SignUpForm from "../../Forms/SignUpForm";

// After
import RegisterButton from "@components/Buttons/RegisterButton";
import SignUpForm from "@components/Forms/SignUpForm";
```
