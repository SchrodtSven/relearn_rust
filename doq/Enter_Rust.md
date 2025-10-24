# Rust me

## A view on variables

- immutable by default (unless ```mut``` is used by declaration)
- variable names could be re-used (this is called <var>shadowing</var>)

```rust
let mut spaces = "   ";
spaces = spaces.len();
```

## Data Types

- scalar
  - integers,
  - floating-point numbers,
  - Booleans, and
  - characters

- compound
  - Tuple
  - Array

### Tuple

```rust
let x: (i32, f64, u8) = (500, 6.4, 1); // implicit tuple declaration
// Now we destructure the tuple (by using its indices)
let five_hundred = x.0;
let six_point_four = x.1;
let one = x.2;
```

### Array

- Fixed length
- All values MUST have the same type

```rust
let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];

// let`s be explicit:
let a: [i32; 5] = [1, 2, 3, 4, 5];

let a = [3; 5]; // same as let a = [3, 3, 3, 3, 3];

```

## Functions

```rust
fn main() {
    print_labeled_measurement(5, 'h');
}

fn print_labeled_measurement(value: i32, unit_label: char) {
    println!("The measurement is: {value}{unit_label}");
}

```

## Statements and Expressions

- **Statements** are instructions that perform some action and *do not return a value*.
- **Expressions** *evaluate to a resultant value*.
