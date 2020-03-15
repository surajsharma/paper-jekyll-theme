---
published: true
---
This quote about git had me inspired:

> The combination of core simplicity and powerful applications often makes thing[s] really hard to grasp, because of the mental jump required to derive the variety of applications from the **essential simplicity of the fundamental abstraction** (monads, anyone?)

It comes from a [tutorial](https://wyag.thb.lt/) on writing your own git in Python, and I decided to port it to TypeScript.

In this and coming posts, we will go through the tutorial and complete it in 8 steps. The code, which is strongly typed to the greatest possible extent can be found [here](https://github.com/inversepolarity/Sustain). The tutorial leaves the task of upgrading the resulting app "_to a full-featured git library and CLI_" to the reader, so we will try to take it a step further, if not all the way.

Shall we dance?

### 0 - Intended Audience
Intermediate JS/TS developers familiar with NodeJS and with at least some basic understanding of File Systems. TypeScript enthusiasts learning the language.

### 1 - Getting Started

The idea is to make a Node.js app in TypeScript that mimics wyag. For this, we will need a CLI interface in TypeScript.

I followed [this tutorial](https://itnext.io/how-to-create-your-own-typescript-cli-with-node-js-1faf7095ef89) on creating a CLI with Node and am summarising the process below:

#### Init

Do an `npm init` in your folder and then add the following dependencies to your `package.json`:

1. [clear](https://www.npmjs.com/package/clear) - clearing the screen, 
2. [figlet](https://www.npmjs.com/package/figlet) - ASCII art for Schwaaag, 
3. [chalk](https://www.npmjs.com/package/chalk) - terminal styling 
4. [commander](https://www.npmjs.com/package/commander) - for args
5. [path](https://www.npmjs.com/package/path) - for working with file and directory paths

and the following devDependencies:

1. [@types/node](https://www.npmjs.com/package/@types/node) - Type definitions for Node.js
2. [nodemon](https://www.npmjs.com/package/nodemon) - If you don't know what this is, now is the time to stop reading this tutorial and go do something else
3. [ts-node](https://www.npmjs.com/package/ts-node) - execution environment and REPL (if you have to google REPL, seriously, please go do something else)
4. [typescript]() - ❤️

#### Scripts

The Scripts section of your `package.json` should look like this:
```
"scripts": {
  "start": "nodemon --watch 'src/**/*.ts' --exec 'ts-node' src/index.ts",
  "create": "npm run build && npm run test",
  "build": "tsc -p .",
  "test": "sudo npm i -g && pizza",
  "refresh": "rm -rf ./node_modules ./package-lock.json && npm install"
},
```

#### TSconfig

You will also need a `tsconfig.json` file in the same folder as your `package.json` with the following contents:
```
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "lib": ["es6", "es2015", "dom"],
    "declaration": true,
    "outDir": "lib",
    "rootDir": "src",
    "strict": true,
    "types": ["node"],
    "esModuleInterop": true,
    "resolveJsonModule": true
  }
}
```
