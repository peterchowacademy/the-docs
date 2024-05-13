---
title: Rust tips - Youtube Shorts
layout: default
parent: Rust 
grand_parent: Coding Practices
---
# Rust tips 

1. No inheritance in Rust [@JeremyChone](https://www.youtube.com/shorts/Fze6w1LbDmc)
> ### Technique used: Data first mindset, using enums

このすば (konosuba)

```rust
// Everything is an algebraic data type, everything is an *object
// Exact opposite of OOP
struct Cat;
struct Dog;

// For a Pet, you present an enum
enum Pet{
    Cat(Cat),
    Dog(Dog)
}

trait Noise{
    fn noise(&self);
}

//For common behaviors, you can provide traits
impl Noise for Cat{
    fn noise(&self){
        println!("Meow");
    }
}

```

2. Data first mindset
```rust
// Populating your struct with data
struct Task{
    id: u64,
    title: String,
    kind: TaskKind,
    desc: Option<Sting>,
}
```
```rust
// Enum works as well
enum WebEvent{
    PageLoad,
    KeyPress(char),
    Paste(String),
    Click{x: i64, y:i64},
}
```