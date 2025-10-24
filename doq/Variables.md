## A view on variables

- immutable by default (unless ```mut``` is used by declaration)
- variable names could be re-used (this is called <var>shadowing</var>)
```rust
let mut spaces = "   ";
spaces = spaces.len();
```