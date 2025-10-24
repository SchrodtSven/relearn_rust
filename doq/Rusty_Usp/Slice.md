# The Slice Type

```rust
fn first_word(s: &String) -> usize {
    let bytes = s.as_bytes();

    for (i, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return i;
        }
    }

    s.len()
}

```

## String Slices

```rust
let s = String::from("hello world");
let hello = &s[0..5];
let world = &s[6..11];
```

<img src="https://doc.rust-lang.org/book/img/trpl04-07.svg" width="400">

### String Slice Syntax examples

With Rust’s .. range syntax, if you want to start at index 0, you can drop the value before the two periods. In other words, these are equal:

```rust
let s = String::from("hello");

let slice = &s[0..2];
let slice = &s[..2];

// By the same token, if your slice includes the last byte of the String, you can drop the trailing number. That means these are equal:

let s = String::from("hello");
let len = s.len();

let slice = &s[3..len];
let slice = &s[3..];

// You can also drop both values to take a slice of the entire string. So these are equal:

let s = String::from("hello");

let len = s.len();

let slice = &s[0..len];
let slice = &s[..];

```

## Other Slices

```rust
// String slices, as you might imagine, are specific to strings. But there’s a more general slice type too. Consider this array:

let a = [1, 2, 3, 4, 5];

//Just as we might want to refer to part of a string, we might want to refer to part of an array. We’d do so like this:

let a = [1, 2, 3, 4, 5];
let slice = &a[1..3];

assert_eq!(slice, &[2, 3]);
```


