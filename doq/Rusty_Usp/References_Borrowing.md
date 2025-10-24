# References & Borrowing

```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{s1}' is {len}.");
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
````

- ```&String```- these ampersands represent *references*, and they allow you to refer to some value <u>without taking ownership</u> of it.

<img src="https://doc.rust-lang.org/book/img/trpl04-06.svg" width ="450">