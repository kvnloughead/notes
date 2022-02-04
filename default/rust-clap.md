---  
Title: rust-clap  
Category: default  
Author: Kevin Loughead  
Date: 2022-01-29  
Tags:   
---  

`clap` is a cli package for rust. 

## Basic usage example (grep clone):

```toml
# Cargo.toml
clap = { version = "3.0", features = ["derive"] }
```

```rust
// main.rs
```

## Notes
With `clap` package, to specify usage, to say you want to use a field for the argument after -o or --output, you’d add `#[clap(short = 'o', long = "output")]`