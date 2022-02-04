---  
Title: error-handling  
Category: rust  
Author: Kevin Loughead  
Date: 2022-01-31  
Tags:   
---  

## Basic error handling
```rust
// handle by panicking
let result = std::fs::read_to_string("test.txt");
let content = match result {
    Ok(content) => { content },
    Err(error) => { panic!("Can't deal with {}, just exit here", error); }
};

// handle by returning error
let result = std::fs::read_to_string("test.txt");
let _content = match result {
    Ok(content) => { content },
    Err(error) => { return Err(error.into()); }
};

// full example
// note that return type of `main` is Result<(), ...>
// this is why we return Err and Ok
fn main() -> Result<(), Box<dyn std::error::Error>> { 
    let result = std::fs::read_to_string("test.txt");
    let content = match result {
        Ok(content) => { content },
        Err(error) => { return Err(error.into()); }
    };
    println!("file content: {}", content);
    Ok(())
}
```

## Shortcuts
```rust
// shortcut for `match` with `panic!`
let content = std::fs::read_to_string("test.txt").unwrap();

// shortcut for `match` that returns error
let content = std::fs::read_to_string("test.txt")?;
```