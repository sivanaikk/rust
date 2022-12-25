# Combinators

#### .map
```rust 

let some_string = Some("LGR".to_owned());
let some_len = some_string.map(|s|
s.len());

struct Error { msg: String }
struct User { name: String }

let string_result: Result<String, Error> =
Ok("Bogdan".to_owned());

let user_result: Result<User, Error> =
    string_result.map(|name| {
        User { name }   
    });
```

#### .and_then

```rust 
let vec = Some(vec![1, 2, 3]);
let first_element = vec.and_then(
    |vec| vec.into_iter().next()
);

let string_result: Result<&'static str, _>
= Ok("5");
let number_result =
    string_result
    .and_then(|s| s.parse::<u32>());
```