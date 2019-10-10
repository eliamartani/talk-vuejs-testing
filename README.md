# Testing VueJS projects

:construction: Under construction :construction:

## About

This little talk is to measure the importance of creating tests on our projects and eventually helping us to avoid from making mistakes in the future

## Tools

Jest, Vue Client, etc.

## Installing Jest through Vue CLI

Execute the following command. Sit and wait 'til everything is done, or just go get a coffee :coffee:

```cmd
vue add @vue/unit-jest
```

It'll create some files structuring the whole project to start working with tests

### Disclaimer

Old projects may face issues since it doesn't use Vue CLI

My suggestion: Install it manually or just add `vue-cli-service` to your project

```cmd
yarn add @vue/cli-service --dev
```

### Installing manually :muscle:

You'll need to install the `jest` packages to your project:

```cmd
yarn add jest jest-transform-stub jest-vue-preprocessor babel-jest vue-jest @vue/test-utils --dev
```

Are you facing `Unexpected token {`? I did...

```cmd
yarn add babel-core babel-jest --dev
```

Now begins the configuration...

`.babelrc`:

```cmd
{
    "presets": [
        "babel-preset-env"
    ]
}
```

`jest.config.js`:

```cmd
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

`package.json`:

```cmd
{
    "scripts": {
        "test": "jest"
    }
}
```

## Testing

> Creating our first test file

## Links

- [@vue/test-utils](https://vue-test-utils.vuejs.org)
- [Unit testing cheat sheet](https://github.com/dekadentno/vue-unit-testing-cheat-sheet)
