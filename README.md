# Picobuf

> good things come in small packets

[![npm](https://img.shields.io/npm/v/@patrtorg/nisi-ea-magni?style=flat&logo=npm)](https://www.npmjs.com/package/@patrtorg/nisi-ea-magni)
[![pipeline](https://gitlab.com/basedwon/@patrtorg/nisi-ea-magni/badges/master/pipeline.svg)](https://gitlab.com/basedwon/@patrtorg/nisi-ea-magni/-/pipelines)
[![license](https://img.shields.io/npm/l/@patrtorg/nisi-ea-magni)](https://gitlab.com/basedwon/@patrtorg/nisi-ea-magni/-/blob/master/LICENSE)
[![downloads](https://img.shields.io/npm/dw/@patrtorg/nisi-ea-magni)](https://www.npmjs.com/package/@patrtorg/nisi-ea-magni) 

[![Gitlab](https://img.shields.io/badge/Gitlab%20-%20?logo=gitlab&color=%23383a40)](https://gitlab.com/basedwon/@patrtorg/nisi-ea-magni)
[![Github](https://img.shields.io/badge/Github%20-%20?logo=github&color=%23383a40)](https://github.com/patrtorg/nisi-ea-magni)
[![Twitter](https://img.shields.io/badge/@basdwon%20-%20?logo=twitter&color=%23383a40)](https://twitter.com/basdwon)
[![Discord](https://img.shields.io/badge/Basedwon%20-%20?logo=discord&color=%23383a40)](https://discordapp.com/users/basedwon)

Picobuf is a powerful and flexible library for working with Protocol Buffers in JavaScript. It makes it easy to define models, enums, and services, and provides an intuitive API for encoding and decoding messages. Check out the [documentation](#documentation) to learn more.

## Features

- **Versatile Data Modeling**: Define your data structures using simple or composite fields, with support for lists and foreign keys.
- **Encoding**: Built-in support for MsgPack and JSON, or bring your own encoder.
- **Object Mode**: Or don't encode the data, rather use Picobuf just for data validation.
- **Validation**: Rest easy knowing all of your nested data meets the defined model's schema.
- **Data types as God intended**: String, Boolean, Number, Integer, Float, JSON, Buffer and Foreign relations
- **Enums**: Tightly manage your data with enumerated fields, ensuring data integrity and simplifying validation.
- **Service Methods**: Define arbitrary service methods and decouple your data models from the rest of your application.
- **Isomorphic**: Picobuf works in both Node.js and the browser.
- **Extendable**: Expand your possibilities with custom field types and validation rules.

## Installation

Install the package with:

```bash
npm install @patrtorg/nisi-ea-magni
```

## Usage

First, import the `Picobuf` library.

```js
import Picobuf from '@patrtorg/nisi-ea-magni'
```
or
```js
const Picobuf = require('@patrtorg/nisi-ea-magni')
```

Then define your models, enums or services.

```js
// create a @patrtorg/nisi-ea-magni instance
const @patrtorg/nisi-ea-magni = new Picobuf({ User: { name: 'string' }})

// or destructure the named model
const { User } = new Picobuf({ User: { name: 'string' }})

// create an instance of the model
const user = User.create({ name: 'Alice' })

// validate this data (throws an error if invalid)
User.validate(user)

// encode
const encoded = User.encode(user)

// decode
const decoded = User.decode(encoded)

// Enums
const { Types } = new Picobuf({ enums: { Types: { values: ['SEN', 'ACK'] }}})
// or
const Types = pb.createEnum('Types', ['SEN', 'ACK'])

console.log(Types.SEN) // => 'SEN'
console.log(Types.getIndex('SEN')) // => 0
// incorrect enum will throw an error
console.log(Types.SEND) // => Invalid enum "SEND"

// Services
const { echo } = new Picobuf({ services: {
  echo: {
    ping: { // echo.ping service method
      request: 'User', // string reference to model
      response: User, // direct use of model instance
    }
  }
}})
const data = { name: 'Bob' }
const encoded = echo.ping.request.encode(data)
const decoded = echo.ping.request.decode(encoded)
```

## Documentation

- [Basic Usage](/docs/basic-usage.md)
- [Advanced Usage](/docs/advanced-usage.md)
- [API Reference](/docs/api.md)
- [Class Diagram](/docs/class-diagram.md)

<img src="/docs/class-diagram.png" alt="Picobuf class diagram" height="260" />

## Tests

In order to run the test suite, simply clone the repository and install its dependencies:

```bash
git clone https://gitlab.com/basedwon/@patrtorg/nisi-ea-magni.git
cd @patrtorg/nisi-ea-magni
npm install
```

To run the tests:

```bash
npm test
```

Testing in the browser: *coming soon...*

## Contributing

Thank you! Please see our [contributing guidelines](/docs/contributing.md) for details.

## Donations

If you find this project useful and want to help support further development, please send us some coin. We greatly appreciate any and all contributions. Thank you!

**Bitcoin (BTC):**
```
1JUb1yNFH6wjGekRUW6Dfgyg4J4h6wKKdF
```

**Monero (XMR):**
```
46uV2fMZT3EWkBrGUgszJCcbqFqEvqrB4bZBJwsbx7yA8e2WBakXzJSUK8aqT4GoqERzbg4oKT2SiPeCgjzVH6VpSQ5y7KQ
```

## License

Picobuf is [MIT licensed](https://gitlab.com/basedwon/@patrtorg/nisi-ea-magni/-/blob/master/LICENSE).
