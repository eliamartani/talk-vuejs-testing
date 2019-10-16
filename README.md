# Testing VueJS projects

## About

In this talk we're going to learn how to setup testing tools at our projects, create tests and eventually realizing the importancy of testing our projects.

## Why test?

????????????????????????????????
????????????????????????????????
????????????????????????????????

## Resons for testing

- Quality Code

*You're sure that the code does what we expect.*

- Design focus on the needs

*You understand the requirements, you design based on that and you build thinking on that.*

- Less debugging more coding

*With more test, few errors you'll have.*

## Tools we're going to use

- Jest
- Vue Client
- Terminal

## Types of Test

- Unit

*The idea of a "unit" in testing, is to break down the code into small, easily testable parts.*

- E2E

*Unlike a unit test, you're testing the entire application.*

- Snapshot

????????????????????????????????
????????????????????????????????
????????????????????????????????

**We're not going to talk about `E2E` and `Snapshot`. For now let's focus on `Unit` testing**

### Comparison between them

????????????????????????????????
????????????????????????????????
????????????????????????????????

## Unit Testing

Quick notes on how to install the testing tool.

### About

### Installing Jest

#### Fastest way (With Vue CLI)

Execute the following command - Sit and wait 'till everything is done, or just go grab a coffee :coffee:

```cmd
vue add @vue/unit-jest
```

It'll add some files so we'll be ready to start working with tests. :raised_hands:

> "Hey buddy, I don't think my project have Vue CLI installed. Can I add it so I won't have that much effort?"

*Hum.... yes?*

Execute the following command... It should work. However I think it may cause an architecture issue, just saying...

```cmd
yarn add @vue/cli-service --dev
```

#### Installing manually :muscle:

You'll need to install the `jest` in your project:

```cmd
yarn add jest jest-transform-stub jest-vue-preprocessor babel-jest vue-jest @vue/test-utils --dev
```

Are you facing `Unexpected token {`? If so, it means your project has a lack of some libraries

```cmd
yarn add babel-core babel-preset-env --dev
```

After that, we need to configure some files so we'll be good to go:

- .babelrc:

```javascript
{
    "presets": [
        "babel-preset-env"
    ]
}
```

- jest.config.js:

```javascript
module.exports = {
    moduleFileExtensions: [
        'js',
        'jsx',
        'json',
        'vue'
    ],
    transform: {
        '^.+\\.vue$': 'vue-jest',
        '.+\\.(css|styl|less|sass|scss|svg|png|jpg|ttf|woff|woff2)$': 'jest-transform-stub',
        '^.+\\.jsx?$': 'babel-jest'
    },
    transformIgnorePatterns: [
        '/node_modules/'
    ],
    moduleNameMapper: {
        '^@/(.*)$': '<rootDir>/resources/js/components/$1'
    },
    testMatch: [
        '**/tests/unit/**/*.spec.(js|jsx|ts|tsx)|**/__tests__/*.(js|jsx|ts|tsx)'
    ]
}
```

- package.json:

```json
{
    "scripts": {
        "test:unit": "jest"
    }
}
```

### How to test it?

The command below will call jest and test everything:

```cmd
yarn test:unit
```

If at some point you're using TDD. Maybe you'll need to add `--watch` and add a new script for that. Just do it!

### Brief explanation

If at this point you still don't know some *keywords* for Javascript testing:

- *describe*: Responsible for grouping every test
- *it*: Where test goes
  - *test*: is an alias. it'll do the same thing
- *expect*: Where comparison is made

### Testing

Live:

> Creating our first test file

Online:

> https://codesandbox.io/s/vue-component-testing-with-jest-ptxbj

### Tips: Testing asynchronous functions

For asynchronous functions we can use `flush-promises`. It flushes all pending resolved promise handlers

Installing:

```cmd
yarn add flush-promises --dev
```

Then adding in your test files:

```javascript
import flushPromises from 'flush-promises'

...

it('async call', async () => {
    wrapper.find('button.add').trigger('click')

    await flushPromises()
    
    expect(something).toBe(true)
})
```

## E2E Testing

:construction: :construction: Under construction :construction: :construction:

Just so you know, this is what an E2E test looks like:

![E2E Test](https://res.cloudinary.com/practicaldev/image/fetch/s--iwFe4sSa--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/wt60c5tp9edask515t1x.png "E2E Test")

*Image from [dev.to](https://dev.to/napoleon039/how-to-test-vue-apps-with-the-popular-cypress-framework-4jfg)*

## Snapshot Testing

????????????????????????????????
????????????????????????????????
????????????????????????????????

## QA

Ask me anything - I'm not that smart but Google is, let's ask him together.

## Links

- [@vue/test-utils](https://vue-test-utils.vuejs.org)
- [Jest cheat sheet](https://github.com/sapegin/jest-cheat-sheet)
- [The What, Why and How of React testing](https://dev.to/mangel0111/the-what-why-and-how-of-react-testing-2702)
- [Unit testing cheat sheet](https://github.com/dekadentno/vue-unit-testing-cheat-sheet)
- [Unit vs E2E Testing for Vue.js](https://vuejsdevelopers.com/2019/04/01/vue-testing-unit-vs-e2e/)

## The end

If you're reading this, I'd like to thank you for the support.

See ya!
