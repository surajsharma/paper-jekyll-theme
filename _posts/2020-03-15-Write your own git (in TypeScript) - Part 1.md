---
published: true
---
This quote about git had me inspired:

> The combination of core simplicity and powerful applications often makes thing[s] really hard to grasp, because of the mental jump required to derive the variety of applications from the **essential simplicity of the fundamental abstraction** (monads, anyone?)

It comes from a [tutorial](https://wyag.thb.lt/) on writing your own git in Python, and I decided to port it to TypeScript.

In this and coming posts, we will go through the tutorial and complete in 8 steps. The code, which is strongly typed to the greatest possible extent can be found [here](https://github.com/inversepolarity/Sustain).

The tutorial leaves the task of upgrading the resulting app "_to a full-featured git library and CLI_" to the reader, so we will try to take it a step further, if not all the way.

Shall we dance?

### 0 - Target Audience
Intermediate JS/TS developers familiar with NodeJS and with at least some basic understanding of File Systems.

### 1 - Getting Started

The idea is to make a NodeJS app in TypeScript that mimics wyag. For this, we will need a CLI interface in TypeScript.

I followed [this tutorial](https://itnext.io/how-to-create-your-own-typescript-cli-with-node-js-1faf7095ef89) on creating a CLI with Node and am summarising the process below:

Do an `npm init` in your folder and then add the following dependencies to your `package.json`:

1. clear - clearing the screen, 
2. figlet - ASCII art for Schwaaag, 
3. chalk - terminal styling 
4. commander - ?
5. path - for working with file and directory paths

and the following devDependencies:

