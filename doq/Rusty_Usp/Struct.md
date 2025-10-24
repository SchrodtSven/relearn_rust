# Structs

## Defining and Instantiating Structs

```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}

fn main() {
    let mut user1 = User { // instantiate struct User as mutable
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
    user1.email = String::from("anotheremail@example.com");
}
```
A tiny function building an active user

```rust
fn build_active_user(email: String, username: String) -> User {
    User {
        active: true,
        username: username,
        email: email,
        sign_in_count: 1,
    }
}

```

## Using the Field Init Shorthand Syntax

The the *field init shorthand syntax* avoids the repetition of ```username``` and ```email```,

```rust
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

## Struct Update Syntax

Using *struct update syntax*, we can achieve the same effect with less code:
```..``` specifies that the remaining fields not explicitly set should have the same value as the fields in the given instance.

```rust
let user2 = User {
    email: String::from("another@example.com"),
    ..user1
}
```

## Example programm using structs

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        area(&rect1)
    );
}

fn area(rectangle: &Rectangle) -> u32 {
    rectangle.width * rectangle.height
}
```
