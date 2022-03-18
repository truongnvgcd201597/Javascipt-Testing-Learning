*What is Jest?*

Jest is a delightful JavaScript Testing Framework with a focus on simplicity.

![](Aspose.Words.991e4c1f-9b95-4dd5-9c31-44424fa491e4.001.png)It works with projects using: [Babel](https://babeljs.io/), [TypeScript](https://www.typescriptlang.org/), [Node](https://nodejs.org/), [React](https://reactjs.org/), [Angular](https://angular.io/), [Vue](https://vuejs.org/) and more!
**Setup Jest Framework:**

Install VSCode Extension:

- [Jest.](https://marketplace.visualstudio.com/items?itemName=Orta.vscode-jest#the-aim)
- [Jest snippets.](https://marketplace.visualstudio.com/items?itemName=andys8.jest-snippets)
- [Jest runner.](https://marketplace.visualstudio.com/items?itemName=firsttris.vscode-jest-runner)

Setup for projects:

--Step 1: NPM initialization.

`npm init`

--Step 2: Install Jest using [Yarn](https://classic.yarnpkg.com/en/package/jest):

`yarn add --dev jest`

*Or [npm](https://www.npmjs.com/package/jest):*

`npm install --save-dev jest.`

We can use export before the code, but since it's an ES6 Module we get an error: "Jest could not parse the file. This happens, for example, when your code or its dependencies use the syntax non-standard Javascript method or when Jest is not configured to support such syntax."

So we'll be using Babel to self-compile converting the ECMAScript 2015+ code into a JavaScript version that's compatible with older JavaScript versions. Babel is a popular tool for using the latest features of the JavaScript programming language. To use Babel, install the required dependencies via Yarn:

`yarn add --dev babel-jest @babel/core @babel/preset-env`

Next, create a babel.config.js file in the root of your project to configure Babel to target the current version of Node:

`module.exports = {`

   `presets: [['@babel/preset-env', {targets: {node: 'current'}}]],`

`};`

