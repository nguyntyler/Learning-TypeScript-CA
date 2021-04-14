# Typescript Basics
## tsconfig.json
This file is always placed in the root of your project. It’s a set of rules that your project must enforce.
```json
{
  "compilerOptions": {
    "target": "es2017",
    "module": "commonjs",
    "strictNullChecks": true
  },
  "include": ["**/*.ts"]
}
```

- `compilerOptions` A nested object that contains the rules for the TypeScript compiler to enforce.
	- `target` **es2017**  means the project will be using the 2017 version of EcmaScript standards for JavaScript.
	- `module` The project will be using **[commonjs](https://nodejs.org/docs/latest/api/modules.html)**  syntax to import and export modules.
	- `strictNullChecks` Variables can only have null or undefined values if they are explicitly assigned those values.
- `includes` Determines what files the compiler applies the rules to. In this case **[“/*.ts”]** means the compiler should check every single file that has a .ts extension.
This also allows us to use the command `tsc` without any arguments in the terminal. The compiler will automatically recognize from tsconfig.json what files to run.
