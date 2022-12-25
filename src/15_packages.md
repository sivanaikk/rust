# Packages, Crates, and Modules


#### Definitions
- Packages - A Cargo feature that lets you build, test, and share crates.
- Crates - A tree of modules that produces a library or executable.
- Modules and use - Let you control the organization, scope, and privacy of paths.
- Paths - A way of naming an item, such as a struct, function, or module.

#### Creating a new package with a binary crate
```bash 
    cargo new my-project
```

#### Creating a new package with a library crate
```bash
cargo new my-project --lib
```
#### Defining and using modules
```rust
fn some_function() {}
mod outer_module { // private module
    pub mod inner_module { // public module
        pub fn inner_public_function() {
            super::super::some_function();
        }
        fn inner_private_function() {}
    }
}

fn main() {
    // absolute path
    crate::outer_module::
    inner_module::inner_public_function();

    // relative path path
    outer_module::
    inner_module::inner_public_function();
    
    // bringing path into scope
    use outer_module::inner_module;
    inner_module::inner_public_function();
}
```
#### Renaming with as keyword

```rust 
use std::fmt::Result;
use std::io::Result as IoResult;
```

#### Re-exporting with pub use

```rust
mod outer_module {
    pub mod inner_module {
        pub fn inner_public_function() {}
    }
}
pub use crate::outer_module::inner_module;
```

#### Defining modules in separate files


```rust
// src/lib.rs
mod my_module;
pub fn some_function() {
my_module::my_function();
}
// src/my_module.rs
pub fn my_function() {}
```