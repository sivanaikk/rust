# Functions, Function Pointers & Closures

#### Associated functions and methods

```rust 
struct Point { x: i32, y: i32, }
impl Point {
// Associated function
fn new(x: i32, y: i32) -> Point {
Point { x: x, y: y }
}
// Method
fn getX(&self) -> i32 { self.x }
}
```

#### Function pointers
```rust
fn do_twice(f: fn(i32) -> i32, arg: i32) ->
i32 {
f(arg) + f(arg)
}
```
#### Creating closures
```rust
let add_one = |num: u32| -> u32 {
    num + 1
};
```
#### Returning closures
```rust
fn add_one() -> impl Fn(i32) -> i32 {
    |x| x + 1
}


fn add_or_subtract(x: i32) -> Box<dyn
    Fn(i32) -> i32> {
    if x > 10 {
        Box::new(move |y| y + x)
    } else {
        Box::new(move |y| y - x)
    }
}
```

#### Closure traits
- FnOnce - consumes the variables it captures from its enclosing scope.
- FnMut - mutably borrows values from its enclosing scope.
- Fn - immutably borrows values from its enclosing scope.

#### Store closure in struct

```rust
struct Cacher<T>
where
T: Fn(u32) -> u32,
{
    calculation: T,
    value: Option<u32>,
}
```

#### Function that accepts closure or function pointer
```rust
fn do_twice<T>(f: T, x: i32) -> i32
where T: Fn(i32) -> i32
{
    f(x) + f(x)
}
```