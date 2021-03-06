## Standard library

ZoKrates comes with a number of reusable components which are defined at `./stdlib/` in the ZoKrates root repository. In order to import the standard library as described in the [imports](./imports.html) section the `$ZOKRATES_HOME` environment variable needs to be set to the `stdlib` folder.  The standard library is solely based on the ZoKrates DSL and can be easily extended.

The following section highlights a subset of available imports:

#### sha256

```zokrates
import "hashes/sha256/512Padded.code"
```

A function that takes 2 `field[256]` arrays as inputs and returns their sha256 compression function as an array of 256 field elements.

#### sha256compression

```zokrates
import "hashes/sha256/512bit.code"
```

A function that takes 2 `field[256]` arrays as inputs and returns their sha256 compression function as an array of 256 field elements.
The difference with `sha256` is that no padding is added at the end of the message, which makes it more efficient but also less compatible with Solidity.

There also is support for 2 round (1024bit input) and and 3 round (1536bit input) variants, using  `hashes/1024bit.code` or `hashes/1536bit.code` respectively.

#### sha256packed

```zokrates
import "hashes/sha256/512bitPacked.code" 
```

A function that takes an array of 4 field elements as inputs, unpacks each of them to 128 bits (big endian), concatenates them and applies sha256. It then returns an array of 2 field elements, each representing 128 bits of the result.

### Direct imports

Some components of the standard library cannot yet be efficiently represented in the ZoKrates DSL language. Those functions are injected at compile-time and are available by default.

#### pack128

```zokrates
import "PACKING/pack128"
```

Packs 128 field elements as one.

#### unpack128

```zokrates
import "PACKING/unpack128"
```

Unpacks a field element to 128 field elements.