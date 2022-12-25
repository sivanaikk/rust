# Control Flow

#### if and if let

```rust
let num = Some(22);

if num.is_some() {
    println!("number is: {}", num.unwrap());
}

// match pattern and assign variable

if let Some(i) = num {
    println!("number is: {}", i);
}
```

### loop

```rust
let mut count = 0;

loop {
    count += 1;
    if count == 5 {
        break; // Exit loop
    }
}
```

#### Nested loops & labels

```rust
'outer: loop {
'inner: loop {
    break;  // This breaks the inner loop
    break 'outer;  // This breaks the outer loop
    }
}
```

#### Returning from loops

```rust
let mut counter = 0;
let result = loop {
    counter += 1;
    if counter == 10 {
        break counter;
    }
};
```

#### while and while let

```rust
while n < 101 {
    n += 1;
}

let mut optional = Some(0);

while let Some(i) = optional {
    print!("{}", i);
}
```

#### for loop

```rust
for n in 1..101 {
    println!("{}", n);
}

let names = vec!["Bogdan", "Wallace"];
for name in names.iter() {
    println!("{}", name);
}
```

#### match

```rust
let optional = Some(0);

match optional {
    Some(i) => println!("{}", i),
    None => println!("No value.")
}
```