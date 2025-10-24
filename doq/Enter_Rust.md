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

fn five() -> i32 {
    5. // no semicolon, it's an expression, not a statement
}

fn main() {
    let x = five();

    println!("The value of x is: {x}");
}

fn main() {
    let x = plus_one(5);

    println!("The value of x is: {x}");
}

fn plus_one(x: i32) -> i32 {
    x + 1
}
```

## Statements and Expressions

- **Statements** are instructions that perform some action and *do not return a value*.
- **Expressions** *evaluate to a resultant value*.

```rust
// the expression inside brackets evaluates to 4
let y = {
        let x = 3;
        x + 1
    };

````

## Control Flow

### ```if``` Expressions

```rust
let condition = true;
let number = if condition { 5 } else { 6 };

println!("The value of number is: {number}");

```

### Repetition with Loops

#### ```loop```

#### Returning Values from Loops

```rust
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {result}");
}
```

#### Loop Labels to Disambiguate Between Multiple Loops

If you have loops within loops, ```break``` and ```continue``` apply to **the innermost loop*** at that point.

```rust
fn main() {
    let mut count = 0;
    'counting_up: loop {
        println!("count = {count}");
        let mut remaining = 10;

        loop {
            println!("remaining = {remaining}");
            if remaining == 9 {
                break;
            }
            if count == 2 {
                break 'counting_up;
            }
            remaining -= 1;
        }

        count += 1;
    }
    println!("End count = {count}");
}

```

### ```while```loop

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;

    while index < 5 {
        println!("the value is: {}", a[index]);

        index += 1;
    }
}

```

### ```for```loop

```rust
 let a = [10, 20, 30, 40, 50];

for element in a {
        println!("the value is: {element}");
}

```

```rust
 for number in (1..4).rev() {
    println!("{number}!");
}
println!("LIFTOFF!!!");
```
