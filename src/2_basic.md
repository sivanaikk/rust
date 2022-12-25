# Basic Types & Variables

- bool - Boolean

- Unsigned integers

    ```
    u8, u16, u32, u64, u128
    ```
- Signed integers
    ```
    i8, i16, i32, i64, i128
    ```
- Floating point numbers
    ```
    f32, f64
    ```
- Platform specific integers
    - ***usize*** - Unsigned integer. Same number of bits as the platform's pointer type.
    - **isize** - Signed integer. Same number of bits as the platform's pointer type.
    - **char** - Unicode scalar value
    - **&str** - String slice
    - **String** - Owned string

#### Tuple

```let coordinates = (82, 64);
let score = ("Team A", 12)
```

#### Array & Slice

- Arrays must have a known length and all
elements must be initialized
```
let array = [1, 2, 3, 4, 5];
let array2 = [0; 3]; // [0, 0, 0]
```

- Unlike arrays the length of a slice is
determined at runtime

```
let slice = &array[1 .. 3];
```

#### HashMap

```
use std::collections::HashMap;
let mut subs = HashMap::new();
subs.insert(String::from("Rust"), 100000);
```

- Insert key if it doesn't have a value

```
subs.entry("Golang".to_owned())
    .or_insert(3);
```

#### Struct

- Definition

```
struct User {
    username: String,
    active: bool,
}
```

- Instantiation

```
let user1 = User {
    username: String::from("bogdan"),
    active: true,
};
```
- Tuple struct

```
struct Color(i32, i32, i32);
let black = Color(0, 0, 0);
```

#### Enum

- Definition

```
enum Command {
    Quit,
    Move { x: i32, y: i32 },
    Speak(String),
    ChangeBGColor(i32, i32, i32),
}
```

- Instantiation

```
let msg1 = Command::Quit;
let msg2 = Command::Move{ x: 1, y: 2 };
let msg3 = Command::Speak("Hi".to_owned());
let msg4 = Command::ChangeBGColor(0, 0, 0);
```

#### Constant

```
const MAX_POINTS: u32 = 100_000;
```

#### Static variable

- Unlike constants static variables are stored in a dedicated memory location and can be mutated.

```
static MAJOR_VERSION: u32 = 1;
static mut COUNTER: u32 = 0;
```

#### Mutability

```
let mut x = 5;
x = 6;
```


#### Shadowing

```
let x = 5;
let x = x * 2;
```

#### Type alias
- *NanoSecond* is a new name for *u64*.

```
type NanoSecond = u64;
```