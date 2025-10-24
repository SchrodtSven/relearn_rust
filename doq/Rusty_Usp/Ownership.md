# USPs

## Ownership

- Each value in Rust has an *owner*.
- There can <u>only be one owner at a time</u>
- When the owner goes *out of scope*, the **value will be dropped**.

### Variable Scope

```rust
 {                      // s is not valid here, since it's not yet declared
    let s = "hello";   // s is valid from this point forward
    // do stuff with s
}                      // this scope is now over, and s is no longer valid


```

In other words, there are two important points in time here:

- When ```s``` comes into scope, it is **valid**.
- It remains valid *until it goes* **out of scope**.

#### Moving 

> [!CAUTION]
> This example won't compile!!!

```rust
let s1 = String::from("hello");
let s2 = s1; // s1 is no longer valid!
println!("{s1}, world!");
```

#### Scope and Assignment

```rust
   let mut s = String::from("hello");
    s = String::from("ahoy");

    println!("{s}, world!");


```
<img src = "https://doc.rust-lang.org/book/img/trpl04-05.svg" width="550">

#### Variables and Data Interacting with Clone

```rust
let s1 = String::from("hello");
let s2 = s1.clone();
println!("s1 = {s1}, s2 = {s2}");
```

#### Stack-Only Data: Copy

> [!NOTE]
> This example works and is valid: **The reason is that types such as integers that have a known size at compile time are stored entirely on the stack, so copies of the actual values are quick to make.**

```rust
let x = 5;
let y = x;
println!("x = {x}, y = {y}");
```
