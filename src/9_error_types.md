# Multiple error types

#### Define custom error type
```rust
type Result<T> = std::result::Result<T,
CustomError>;

#[derive(Debug, Clone)]
struct CustomError;

impl fmt::Display for CustomError {
fn fmt(&self, f: &mut fmt::Formatter) ->
    fmt::Result {
        write!(f, "custom error message")
    }
}
```

#### Boxing errors
```rust
use std::error;

type Result<T> = std::result::Result<T,
Box<dyn error::Error>>;
```