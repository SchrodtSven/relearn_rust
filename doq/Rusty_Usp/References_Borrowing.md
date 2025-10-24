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

> [!IMPORTANT]
> Just as variables are **immutable by default, so are references**. We’re not allowed to modify something we have a reference to.

## Mutable References

- First we change ```s``` to be ```mut```
- Then we create a mutable reference with ```&mut s``` where we call the ```change``` function, and
- update the function signature to accept a mutable reference with ```some_string: &mut String```.
- This makes it very clear that the change function will mutate the value it borrows.

```rust
fn main() {
    let mut s = String::from("hello");

    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

> [!IMPORTANT]
> Mutable references have one big restriction: if you have a mutable reference to a value, **you can have no other references to that value**. This code that attempts to create two mutable references to ```s``` will fail

## The Rules of References

Let’s recap what we’ve discussed about references:

- At any given time, you can have either one mutable reference or any number of immutable references.
- References must always be valid.
