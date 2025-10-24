# References & Borrowing

```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{s1}' is {len}.");
}

fn calculate_length(s: &String) -> usize {
    s.len()
} // Here, s goes out of scope. But because s does not have ownership of what
  // it refers to, the String is not dropped.
````

- ```&String```- these ampersands represent *references*, and they allow you to refer to some value <u>without taking ownership</u> of it.

<img src="https://doc.rust-lang.org/book/img/trpl04-06.svg" width ="450">

> [!CAUTION]
> This example won't compile!!!

```rust
fn main() {
    let s = String::from("hello");

    change(&s);
}

fn change(some_string: &String) {
    some_string.push_str(", world");
}
```

> [!INFO]
> Just as variables are immutable by default, so are references. We’re not allowed to modify something we have a reference to.