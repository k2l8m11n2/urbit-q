# urbit-q

Based on [urbit-ob](https://github.com/urbit/urbit-ob), supports only the `@q` format.

## usage

Note that `encode` pads the beginning to an even number of bytes (as per the
original implementation) and `decode` ignores any dashes or spaces within the
string.
```rust
let bytes: [u8; 3] = [1, 2, 3];
let string = urbit_q::encode(&bytes); // doznec-binwes
urbit_q::decode(&string).unwrap(); // [0, 1, 2, 3]
urbit_q::decode("doz nec bin wes"); // Some([0, 1, 2, 3])
urbit_q::decode("do-z ne cb inwes"); // Some([0, 1, 2, 3])
urbit_q::decode("hello world"); // None
```