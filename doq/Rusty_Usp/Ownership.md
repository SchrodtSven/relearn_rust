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

### Ownership and Functions

```rust
fn main() {
    let s = String::from("hello");  // s comes into scope

    takes_ownership(s);             // s's value moves into the function...
                                    // ... and so is no longer valid here

    let x = 5;                      // x comes into scope

    makes_copy(x);                  // Because i32 implements the Copy trait,
                                    // x does NOT move into the function,
                                    // so it's okay to use x afterward.

} // Here, x goes out of scope, then s. However, because s's value was moved,
  // nothing special happens.

fn takes_ownership(some_string: String) { // some_string comes into scope
    println!("{some_string}");
} // Here, some_string goes out of scope and `drop` is called. The backing
  // memory is freed.

fn makes_copy(some_integer: i32) { // some_integer comes into scope
    println!("{some_integer}");
} // Here, some_integer goes out of scope. Nothing special happens.
```
#### Return Values and Scope

```rust
fn main() {
    let s1 = gives_ownership();        // gives_ownership moves its return
                                       // value into s1

    let s2 = String::from("hello");    // s2 comes into scope

    let s3 = takes_and_gives_back(s2); // s2 is moved into
                                       // takes_and_gives_back, which also
                                       // moves its return value into s3
} // Here, s3 goes out of scope and is dropped. s2 was moved, so nothing
  // happens. s1 goes out of scope and is dropped.

fn gives_ownership() -> String {       // gives_ownership will move its
                                       // return value into the function
                                       // that calls it

    let some_string = String::from("yours"); // some_string comes into scope

    some_string                        // some_string is returned and
                                       // moves out to the calling
                                       // function
}

// This function takes a String and returns a String.
fn takes_and_gives_back(a_string: String) -> String {
    // a_string comes into
    // scope

    a_string  // a_string is returned and moves out to the calling function
}
```

```rust
fn main() {
    let s1 = String::from("hello");

    let (s2, len) = calculate_length(s1);

    println!("The length of '{s2}' is {len}.");
}

fn calculate_length(s: String) -> (String, usize) {
    let length = s.len(); // len() returns the length of a String

    (s, length) // returning multiple values as tuple
}
````

> [!TIP]
> [References & Borrowing](References_Borrowing.md)