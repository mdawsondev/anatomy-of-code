# Standard Built-in Objects
###### Sourced through [MDN][0].

The **global object** wraps the topmost scope, and in the case of a browser application is the `window` object. **Global objects**, on the other hand, sit *within* the global object. The global object can be accessed through `this` in the global scope as long as `'use strict';` hasn't been envoked. 

## Value Objects
* [Infinity](../docs/Global%20Objects/Infinity.md)
* NaN
* undefined
* null

## Function Objects
* eval()
* uneval() ⚠
* isFinite()
* isNaN()
* parseFloat()
* parseInt()
* decodeURIComponent()
* encodeURI()
* encodeURIComponent()
* ~~[escape()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/escape)~~
* ~~[unescape()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/unescape)~~

## Fundamental Objects
* Object
* Function
* Boolean
* Symbol
* Error
* EvalError
* InternalError
* RangeError
* ReferenceError
* SyntaxError
* TypeError
* URIError

## Numbers and Dates
* Number
* Math
* Date

## Text Processing
* String
* RegExp

## Indexed Collections
* Array
* Int8Array
* Uint8Array
* Unit8ClampedArray
* Init16Array
* Uinit16Array
* Init32Array
* Uinit32Array
* Float32Array
* Float64Array

## Keyed Collections
* Map
* Set
* WeakMap
* WeakSet

## Vector Collections
* SIMD ⚠
* SIMD.Float32x4 ⚠
* SIMD.Float64x2 ⚠
* SIMD.Int8x16 ⚠
* SIMD.Int16x8 ⚠
* SIMD.Int32x4 ⚠
* SIMD.Uint8x16 ⚠
* SIMD.Uint16x8 ⚠
* SIMD.Uint32x4 ⚠
* SIMD.Bool8x16 ⚠
* SIMD.Bool16x8 ⚠
* SIMD.Bool32x4 ⚠
* SIMD.Bool64x2 ⚠

## Structured Data
* ArrayBuffer
* SharedArrayBuffer ⚠
* Atomics ⚠
* DataView
* JSON

## Control Abstraction Objects
* Promise
* Generator
* GeneratorFunction
* AsyncFunction ⚠

## Reflection
* Reflect
* Proxy

## Internationalization
* Intl
* Intl.Collator
* Intl.DateTimeFormat
* Intl.NumberFormat

## WebAssembly
* WebAssembly
* WebAssembly.Module
* WebAssembly.Instance
* WebAssembly.Memory
* WebAssembly.Table
* WebAssembly.CompileError
* WebAssembly.LinkError
* WebAssembly.RuntimeError

## Other
* arguments

[0]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects