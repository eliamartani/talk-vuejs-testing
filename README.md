# Testing VueJS projects

## About

This little talk is to measure the importance of creating tests on our projects and eventually helping us to avoid from making mistakes in the future

## Resons for testing



## Tools we're going to use

- Jest
- Vue Client

## Types of Test

- `Unit testing`

> *The idea of a "unit" in testing, is to break down the code into small, easily testable parts.*

- `E2E testing`

> *Unlike a unit test, you're testing the entire application.*

**We're not going to talk about `E2E`. Sorry!**

## Unit Testing

### Installing Jest

#### Fastest way - With Vue CLI

Execute the following command - Sit and wait 'till everything is done, or just go grab a coffee :coffee:

```cmd
vue add @vue/unit-jest
```

It will create some files structuring the whole project to just start working with tests.

> "Hey buddy, I'm kinda lazy and I think my project doesn't have Vue CLI. Can I add it so I don't have to think too much?"

Hum.... yes? Execute the following command. It should work.

```cmd
yarn add @vue/cli-service --dev
```

#### Installing manually :muscle:

You'll need to install the `jest` package in your project:

```cmd
yarn add jest jest-transform-stub jest-vue-preprocessor babel-jest vue-jest @vue/test-utils --dev
```

Are you facing `Unexpected token {`? *I faced...*

```cmd
yarn add babel-core babel-preset-env --dev
```

Now begins the configuration...

- `.babelrc`:

```javascript
{
    "presets": [
        "babel-preset-env"
    ]
}
```

- `jest.config.js`:

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

- `package.json`:

```json
{
    "scripts": {
        "test:unit": "jest"
    }
}
```

### How to test it?

Execute:

```cmd
yarn test:unit
```

### Brief explanation

- `describe`: Responsible for grouping every test
- `it` or `test`: Where test goes
- `describe`: Where comparison is made

### Testing

> Creating our first test file

### Testing asynchronous functions

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

## Links

- [@vue/test-utils](https://vue-test-utils.vuejs.org)
- [Jest cheat sheet](https://github.com/sapegin/jest-cheat-sheet)
- [Unit testing cheat sheet](https://github.com/dekadentno/vue-unit-testing-cheat-sheet)
- [Unit vs E2E Testing for Vue.js](https://vuejsdevelopers.com/2019/04/01/vue-testing-unit-vs-e2e/)
