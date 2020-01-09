# xsalsa20

XSalsa20 implemented in Javascript and WebAssembly.

```
npm install xsalsa20
```

[![build status](https://travis-ci.org/mafintosh/xsalsa20.svg?branch=master)](https://travis-ci.org/mafintosh/xsalsa20)


## Usage

``` js
var crypto = require('crypto')
var xsalsa20 = require('xsalsa20')
var key = crypto.randomBytes(32)
var nonce = crypto.randomBytes(24)

var xor = xsalsa20(nonce, key)

console.log(xor.update(new Buffer('hello')))
console.log(xor.update(new Buffer('world')))

xor.finalize()
```

## API

#### `var xor = xsalsa20(nonce, key)`

Create a new xor instance.

Nonce should be a 24 byte buffer/uint8array and key should be 32 bytes.

#### `var output = xor.update(input, [output])`

Update the xor instance with a new input buffer. Optionally you can pass in an output buffer.

#### `xor.finalize()`

Call this method last. Clears internal state.

## Building

The WAT file is built using [wat2js](https://github.com/mafintosh/wat2js) called from the prepare hook.  This requires the [webassembly-binary-toolkit](https://github.com/mafintosh/webassembly-binary-toolkit) to be installed globally.

## License

MIT
