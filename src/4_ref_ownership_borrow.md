# References, Ownership, and Borrowing

### Ownership rules

1. Each value in Rust has a variable that’s called its
owner.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will
be dropped.

### Borrowing rules

1. At any given time, you can have either one mutable reference or any number of immutable references.
2. References must always be valid. 

#### Creating references

```rust
let s1 = String::from("hello world!");
let s1_ref = &s1; // immutable reference
let mut s2 = String::from("hello");
let s2_ref = &mut s2; // mutable reference
s2_ref.push_str(" world!");
```

#### Copy, Move, and Clone
- Simple values which implement the Copy
trait are copied by value

```rust
let x = 5;
let y = x;

println!("{}", x); // x is still valid. The string is moved to s2 and s1 is invalidated

let s1 = String::from("Rust Notes");
let s2 = s1; // Shallow copy a.k.a move

println!("{}", s1); // Error: s1 is invalid

let s1 = String::from("Rust Notes");
let s2 = s1.clone(); // Deep copy

// Valid because s1 isn't moved
println!("{}", s1);
```

#### Ownership and functions
```rust
fn main() {
    let x = 5;
    takes_copy(x); // x is copied by value
    let s = String::from("Rust Notes");
    // s is moved into the function
    takes_ownership(s);
    // return value is moved into s1
    let s1 = gives_ownership();
    let s2 = String::from("Rust");
    let s3 = takes_and_gives_back(s2);
}

fn takes_copy(some_integer: i32) {
    println!("{}", some_integer);
}

fn takes_ownership(some_string: String) {
    println!("{}", some_string);
} // some_string goes out of scope and drop is called. The backing memory is freed.

fn gives_ownership() -> String {
    let some_string = String::from("Rust");
    some_string
}

fn takes_and_gives_back(some_string:
    String) -> String {
    some_string
}
```