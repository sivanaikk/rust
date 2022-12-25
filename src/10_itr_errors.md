# Iterating over errors

#### Ignore failed items with filter_map()

```rust 
let strings = vec!["LGR", "22", "7"];

let numbers: Vec<_> = strings
    .into_iter()
    .filter_map(|s| s.parse::<i32>().ok())
    .collect();
```

#### Fail the entire operation with collect()
```rust 
let strings = vec!["LGR", "22", "7"];

let numbers: Result<Vec<_>, _> = strings
    .into_iter()
    .map(|s| s.parse::<i32>())
    .collect();
```

#### Collect all valid values and failures with partition()

```rust
let strings = vec!["LGR", "22", "7"];

let (numbers, errors): (Vec<_>, Vec<_>) =
strings
.into_iter()
    .map(|s| s.parse::<i32>())
    .partition(Result::is_ok);

let numbers: Vec<_> = numbers
    .into_iter()
    .map(Result::unwrap)
    .collect();
    
let errors: Vec<_> = errors
    .into_iter()
    .map(Result::unwrap_err)
    .collect();
```