# Iterators

#### Usage

```rust
// Methods that consume iterators
let v1 = vec![1, 2, 3];
let v1_iter = v1.iter();
let total: i32 = v1_iter.sum();

// Methods that produce new iterators
let v1: Vec<i32> = vec![1, 2, 3];
let iter = v1.iter().map(|x| x + 1);

// Turning iterators into a collection
let v1: Vec<i32> = vec![1, 2, 3];
let v2: Vec<_> = v1.iter().map(|x| x +
1).collect();
```

#### Implementing the Iterator trait

```rust
struct Counter {
    count: u32,
}

impl Counter {
    fn new() -> Counter {
        Counter { count: 0 }
    }
}

impl Iterator for Counter {
    type Item = u32;
    
    fn next(&mut self) -> Option<Self::Item>
    {
        if self.count < 5 {
            self.count += 1;
            Some(self.count)
        } else {
            None
        }
    }
}
```