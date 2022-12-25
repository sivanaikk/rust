# Pointers

#### References
```rust

let mut num = 5;
let r1 = &num; // immutable reference
let r2 = &mut num; // mutable reference
```
#### Raw pointers

```rust
let mut num = 5;
// immutable raw pointer
let r1 = &num as *const i32;
// mutable raw pointer
let r2 = &mut num as *mut i32;
```