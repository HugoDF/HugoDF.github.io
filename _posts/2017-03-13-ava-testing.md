---
layout: post
title: "AVA, low-config testing for JavaScript"
date:   2017-03-13 10:25:00
categories: javascript, front-end, testing, ES6
---

## A JavaScript testing library for 2017

[AVA](https://github.com/avajs/ava) is a Futuristic JavaScript test runner.

Some of its best features are:
- it works out of the box, no need to specify a blob for test files or add Babel hooks
- it’s runs tests in parallel, this stops you from using global state and runs faster
- the tests are async by default

I quite like AVA since I can just drop it in and reap benefits without too much hassle. I’ve never had to fight against AVA to get tests running, that means more focus on the code and tests and less on the setup.

# No blob configuration

Running AVA at the command line is as simple as (if you’ve got it installed globally):

```
$ ava
```

To run AVA in watch mode at the command line:

```
$ ava -w
```

To run AVA in verbose mode:
```sh
$ ava --verbose
```

If your test files match against `test.js test-*.js test/**/*.js **/__tests__/**/*.js **/*.test.js` AVA will pick them up and run them. You can always override this, but I don’t think you would want to configure AVA differently.

We can wrap these commands in a npm scripts and use the project’s version of AVA. And actually AVA has a command that can add this stuff to your `package.json`:

```
$ ava --init
```

It will add AVA in `devDependencies` and in test script.

# Visibility where it matters

Here is an example test file in Mocha:

```
const { expect } = require('chai');
describe('Some function', () => {
  it('does something with input', () => {
    const actualOutput = 42;
    const expectedOutput = 42;
    expect(actualOutput).to.equal(expectedOutput);
  });
});
```

`describe`?`it`? Not so obvious that they’re functions defined by the test runner. We’re also using chai for our assertions… Wouldn’t it be nice if all this was one package and it was obvious we were using it?

Mocha best practices also say we shouldn’t be using arrow functions (`() => {}`) since we may want to access the `this` defined inside of describe or it instead of the global module `this`.

Here is the same test in AVA:

```
import test from 'ava';
test('Some function', t => {
    const actualOutput = 42;
    const expectedOutput = 42;
    t.equal(actualOutput, expectedOutput);
});
```

AVA is less verbose, it does the job of the assertion library and is the test runner at the same time. We’re relying on a this anywhere since the test object `t` is passed as a parameter.

There is no nesting in AVA, it uses the test file and its path to define test suites.

# Hooks for current and future JavaScript
AVA runs using full ES2016 syntax by default and runs its code through Babel transforms.
This means, without adding a Babel hook (like you would in Mocha) you can write:

```
import test from 'ava';
import sinon from 'sinon';
test('It actually runs', t => {
  t.pass();
});
```
When you run the tests:

```
$ ava
  1 passed
```
No syntax error on the ‘import’ statement.
If you’re importing components that need to be Babel transformed (React components using JSX for example), you just need to add the following Babel hook to the AVA config in package.json:

```
{
  "ava": {
    "require": [
      "babel-register"
    ],
    "babel": "inherit"
  }
}
```

This means it’s easy to write modern JavaScript and test it using the same syntax and minimal headaches using AVA.

# Async by default

No more Promisifying your assertions, no more passing done callbacks, well sort of.
If you use promises, AVA loves it:

```
import test from 'ava';
test('Promise resolves to correct value', t => 
  return new Promise(resolve => resolve(1))
    .then(value => {
      t.is(value, 1)
    });
});
```

If you want to use async, even better:

```
import test from 'ava';
test('Promise resolves to correct value', async t => {
  const promiseResolution = new Promise(resolve => resolve(1));
  t.is(await promiseResolution, 1);
});
```

And you have the good old callback mode, which works fine, you obviously have to call and .end somewhere like any other test runner:

```
import test from 'ava';
test.cb('Callback gets correct value', t => {
  t.plan(1);
  setTimeout(() => {
    t.pass();
    t.end();
  }, 100);
});
```

In the async cases, you can use t.plan to specify the number of assertions that should be run, it will fail if that exact number of assertions isn’t run . This is different to some other test runner that will fail if less than the specified number of assertions are run.

# Conclusion
AVA is low-config, low maintenance testing for JavaScript for 2017 and beyond. You get really nice diffs on failed assertions, a one-library solution for assertions and running tests. The tests run fast and promote best practice (pure tests) and are ready to test async functionality out of the box.

Feel free to share this post if you found it useful. You can find me on Twitter [@hugo__df](https://twitter.com/hugo__df).

[AVA, low-config testing for JavaScript](https://blog.hellojs.org/ava-low-config-testing-for-javascript-71bd2d958745) was originally published at [https://medium.com/@hugo__df](https://medium.com/@hugo__df) on 13th March 2017.



Recent JavaScript/Developer Productivity posts:

[Visual Studio Code: the editor I didn’t think I needed](https://hackernoon.com/virtualstudio-code-the-editor-i-didnt-think-i-needed-16970c8356d5)

[Effective Functional JavaScript: First-class and Higher Order Functions](https://hackernoon.com/effective-functional-javascript-first-class-and-higher-order-functions-713fde8df50a)