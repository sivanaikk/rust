# Generics, Traits, and Lifetimes

#### Using generics

```rust 
struct Point<T, U> {
    x: T,
    y: U,
}

impl<T, U> Point<T, U> {
    fn mixup<V, W>(self, other: Point<V, W>)
-> Point<T, W> {
        Point {
            x: self.x,
            y: other.y,
        }
    }
}

```
#### Defining traits
```rust
trait Animal {
    fn new(name: &'static str) -> Self;
    fn noise(&self) -> &'static str { "" }
}

struct Dog { name: &'static str }

impl Dog {
    fn fetch() { // ... }
}

impl Animal for Dog {
    fn new(name: &'static str) -> Dog {
        Dog { name: name }
    }

    fn noise(&self) -> &'static str {
        "woof!"
    }
}
```

#### Default implementations with Derive
```rust 
// A tuple struct that can be printed
#[derive(Debug)]
struct Inches(i32);
```

#### Trait bounds
```rust
fn largest<T: PartialOrd + Copy>(list:
&[T]) -> T {
    let mut largest = list[0];
    for &item in list {
        if item > largest {
            largest = item;
        }
    }
    largest
}
```

#### impl trait
```rust
fn make_adder_function(y: i32) -> impl
Fn(i32) -> i32 {
    let closure = move |x: i32| { x + y };
    closure
}
```
#### Trait objects
```rust
pub struct Screen {
    pub components: Vec<Box<dyn Draw>>,
}
```
#### Operator overloading
```rust
use std::ops::Add;

#[derive(Debug, Copy, Clone, PartialEq)]
struct Point {
    x: i32,
    y: i32,
}

impl Add for Point {
    type Output = Point;
    fn add(self, other: Point) -> Point {
        Point {
            x: self.x + other.x,
            y: self.y + other.y,
        }   
    }
}
```

#### Supertraits

```rust
use std::fmt;

trait Log: fmt::Display {
    fn log(&self) {
        let output = self.to_string();
        println!("Logging: {}", output);
    }
}
```

#### Lifetimes in function signatures

```rust
fn longest<'a>(x: &'a str, y: &'a str) ->
&'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

#### Lifetimes in struct definitions

```rust
struct User<'a> {
    full_name: &'a str,
}
```

#### Static lifetimes
```rust
let s: &'static str = "Rust";
```