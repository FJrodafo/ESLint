## Index

1. [Attribution](#attribution)
2. [Installation](#installation)
3. [Basic configuration](#basic-configuration)
4. [My configuration](#my-configuration)
5. [Run it!](#run-it)

## Attribution

This project was build by following the [discord.js guide](https://discordjs.guide/preparations/setting-up-a-linter.html). I have modified small details of the code. This is just an example of what the final project would look like.

## Installation

Install the [ESLint package](https://www.npmjs.com/package/eslint) inside your project directory (Make sure you are in the `App` directory):

```shell
npm install --save-dev eslint
```

## Basic configuration

The basic syntax of the linter must be written in the `.eslintrc.json` file. Below is an example:

```json
{
    "extends": "eslint:recommended",
    "env": {
        "node": true,
        "es6": true
    },
    "parserOptions": {
        "ecmaVersion": 2021
    },
    "rules": {

    }
}
```

This is the basis of how an ESLint file will look. The `rules` object is where you'll define what rules you want to apply to ESLint. For example, if you want to make sure you never miss a semicolon, the `"semi": ["error", "always"]` rule is what you'll want to add inside that object:

```json
{
    "extends": "eslint:recommended",
    "env": {
        "node": true,
        "es6": true
    },
    "parserOptions": {
        "ecmaVersion": 2021
    },
    "rules": {
        "semi": ["error", "always"]
    }
}
```

## My configuration

You can find a list of all of ESLint's rules on [their website](https://eslint.org/docs/rules). There are indeed many rules, and it may be overwhelming at first, so if you don't want to go through everything on your own yet, you can use these rules:

```json
{
    "extends": "eslint:recommended",
    "env": {
        "node": true,
        "es6": true
    },
    "parserOptions": {
        "ecmaVersion": 2021
    },
    "rules": {
        "arrow-spacing": ["warn", { "before": true, "after": true }],
        "brace-style": ["error", "stroustrup", { "allowSingleLine": true }],
        "comma-dangle": ["error", "always-multiline"],
        "comma-spacing": "error",
        "comma-style": "error",
        "curly": ["error", "multi-line", "consistent"],
        "dot-location": ["error", "property"],
        "handle-callback-err": "off",
        "indent": ["error", "tab"],
        "keyword-spacing": "error",
        "max-nested-callbacks": ["error", { "max": 4 }],
        "max-statements-per-line": ["error", { "max": 2 }],
        "no-console": "off",
        "no-empty-function": "error",
        "no-floating-decimal": "error",
        "no-inline-comments": "error",
        "no-lonely-if": "error",
        "no-multi-spaces": "error",
        "no-multiple-empty-lines": ["error", { "max": 2, "maxEOF": 1, "maxBOF": 0 }],
        "no-shadow": ["error", { "allow": ["err", "resolve", "reject"] }],
        "no-trailing-spaces": ["error"],
        "no-var": "error",
        "object-curly-spacing": ["error", "always"],
        "prefer-const": "error",
        "quotes": ["error", "single"],
        "semi": ["error", "always"],
        "space-before-blocks": "error",
        "space-before-function-paren": ["error", {
            "anonymous": "never",
            "named": "never",
            "asyncArrow": "always"
        }],
        "space-in-parens": "error",
        "space-infix-ops": "error",
        "space-unary-ops": "error",
        "spaced-comment": "error",
        "yoda": "error"
    }
}
```

The major points of this setup would be:

- Allowing you to debug with console.log();
- Prefer using const over let or var, as well as disallow var;
- Disapproving of variables with the same name in callbacks;
- Requiring single quotes over double quotes;
- Requiring semicolons. While not required in JavaScript, it's considered one of the most common best practices to follow;
- Requiring accessing properties to be on the same line;
- Requiring indenting to be done with tabs;
- Limiting nested callbacks to 4. If you hit this error, it is a good idea to consider refactoring your code.

If your current code style is a bit different, or you don't like a few of these rules, that's perfectly fine! Just head over to the [ESLint docs](https://eslint.org/docs/rules/), find the rule(s) you want to modify, and change them accordingly.

## Run it!

There is a special command located in the `package.json` file that runs the ESLinter:

```json
{
  "scripts": {
    "eslint": "eslint './**/*.js'",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "devDependencies": {
    "eslint": "^8.56.0"
  }
}
```

Once you have pasted your JavaScript code that you want to be analyzed by ESLint in the `main.js` file, you can proceed to write the following command in the console (Make sure you are in the `App` directory):

```shell
npm run eslint
```

If you decide to run the command with the example code provided in the `main.js` file, ESLint will show you the errors that the code has following the configuration previously established in the `.eslintrc.json` file. All that remains is to gradually fix the errors shown by the console.

```
╭╴fjrodafo@linux[App](main)
╰─╴$ npm run eslint

> eslint
> eslint './**/*.js'


/home/fjrodafo/Documents/Repos/ESLint/App/src/main.js
   3:1   error  Unexpected var, use let or const instead                              no-var
   3:15  error  Missing semicolon                                                     semi
   4:15  error  Missing semicolon                                                     semi
   7:16  error  Strings must use singlequote                                          quotes
   8:16  error  Strings must use singlequote                                          quotes
   8:27  error  Missing trailing comma                                                comma-dangle
   9:2   error  Missing semicolon                                                     semi
  13:26  error  Missing semicolon                                                     semi
  14:5   error  Closing curly brace appears on the same line as the subsequent block  brace-style
  15:26  error  Missing semicolon                                                     semi
  17:1   error  Closing curly brace appears on the same line as the subsequent block  brace-style
  18:23  error  Missing semicolon                                                     semi
  21:19  error  Missing semicolon                                                     semi

✖ 13 problems (13 errors, 0 warnings)
  13 errors and 0 warnings potentially fixable with the `--fix` option.
```

Once all the errors in the example code have been corrected, it would look like this (type `npm run eslintfix` to fix errors automatically):

```js
let num1, num2;
let num3, num4;

const array = [
    { Object1: 'Object1' },
    { Object2: 'Object2' },
];

try {
    if (num1 > num2) {
        console.log(num3);
    }
    else {
        console.log(num4);
    }
}
catch (error) {
    console.log(error);
}

console.log(array);
```

<link rel="stylesheet" href="./README.css">
<a class="scrollup" href="#top">&#x1F53C</a>