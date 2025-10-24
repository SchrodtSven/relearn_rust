# Method Syntax

- Methods are similar to functions
- being declared them with the ```fn``` keyword and a name,
- can have parameters and a return value
- contain some code that’s run when the method is called from somewhere else. 

- **Unlike functions**:
    - methods are defined within the **context of a struct** (or an enum or a trait object)
    - their first parameter is always ```self``` self, which represents the instance of the struct the method is being called on - Holy 🐍!

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        rect1.area()
    );
}

```

- The implementation ```impl``` part is named like the struct
- Everything in the scope (between curly brackets) has the context of this struct (```Rectangle```)
- ```fn``` area defines a method within this context
- the method's signature use ```&self```
    - instead of ```rectangle: &Rectangle```
    - being short for ```self: &Self```
    - the ```&``` in front of ```self``` indicates, that this method borrows the ```Self``` instance

## Multiple impl Blocks

```rust

```