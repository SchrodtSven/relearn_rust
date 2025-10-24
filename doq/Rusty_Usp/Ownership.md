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

> [!WARN]
> This example won't compile!!!

```rust
let s1 = String::from("hello");
let s2 = s1; // s1 is no longer valid!
println!("{s1}, world!");
```
