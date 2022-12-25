# Error Handling

#### Throw unrecoverable error

```rust
panic!("Critical error! Exiting!");
```

#### Option enum

```rust
fn get_user_id(name: &str) -> Option<u32> {
    if database.user_exists(name) {
        return Some(database.get_id(name))
    }

    None
}
```

#### Result enum
```rust
fn get_user(id: u32) -> Result<User, Error>
{
    if is_logged_in_as(id) {
        return Ok(get_user_object(id))
    }

    Err(Error { msg: "not logged in" })
}
```

#### ? operator
```rust
fn get_salary(db: Database, id: i32) ->
Option<u32> {
    Some(db.get_user(id)?.get_job()?.salary)
}

fn connect(db: Database) ->
Result<Connection, Error> {
let conn = db.get_active_instance()?.connect()?;
    Ok(conn)
}
```