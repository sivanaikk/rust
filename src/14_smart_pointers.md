# Smart pointers

#### Box<T>
- for allocating values on the heap
```rust
let b = Box::new(5);
```

#### Rc<T> 
- multiple ownership with reference counting
```rust 
let a = Rc::new(5);
let b = Rc::clone(&a);
```

#### Ref<T>, RefMut<T>, and RefCell<T>
- enforce borrowing rules at runtime instead of compile time.
```rust
let num = 5;
let r1 = RefCell::new(5);
// Ref - immutable borrow
let r2 = r1.borrow();
// RefMut - mutable borrow
let r3 = r1.borrow_mut();
// RefMut - second mutable borrow
let r4 = r1.borrow_mut();
```

#### Multiple owners of mutable data
```rust
let x = Rc::new(RefCell::new(5));
```