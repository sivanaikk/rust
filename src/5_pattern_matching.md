# Pattern Matching

### Basics

```rust 
let x = 5;
match x {
    // matching literals
    1 => println!("one"),

    // matching multiple patterns
    2 | 3 => println!("two or three"),
    
    // matching ranges
    4..=9 => println!("within range"),
    
    // matching named variables
    x => println!("{}", x),
    
    // default case (ignores value)
    _ => println!("default Case")
}
```

#### Destructuring


```rust 
struct Point {
    x: i32,
    y: i32,
}

let p = Point { x: 0, y: 7 };

match p {
    Point { x, y: 0 } => {
        println!("{}" , x); 
    },

    Point { x, y } => {
        println!("{} {}" , x, y);
    },
}

enum Shape {
    Rectangle { width: i32, height: i32 },
    Circle(i32),
}

let shape = Shape::Circle(10);
match shape {
    Shape::Rectangle { x, y } => //...
    Shape::Circle(radius) => //...
}
```

#### Ignoring values

```rust 
struct SemVer(i32, i32, i32);
    let version = SemVer(1, 32, 2);
    match version {
    SemVer(major, _, _) => {
        println!("{}", major);
    }
}

let numbers = (2, 4, 8, 16, 32);
match numbers {
        (first, .., last) => {
            println!("{}, {}", first, last);
        }
}
```

#### Match guards

```rust
let num = Some(4);
match num {
    Some(x) if x < 5 => println!("less than five: {}", x),
    Some(x) => println!("{}", x),
    None => (),
}
```

### @ bindings
```rust
struct User {
    id: i32
}
let user = User { id: 5 };
match user {
    User {
        id: id_variable @ 3..=7,
    } => println!("id: {}", id_variable),
    User { id: 10..=12 } => {
        println!("within range");
    },
    User { id } => println!("id: {}", id),
}
```