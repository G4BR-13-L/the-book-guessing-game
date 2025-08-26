# 🎲 Guessing Game in Rust

This repository contains the **first project** from *[The Rust Programming Language Book](https://doc.rust-lang.org/book/)* — a simple **number guessing game**.

The program randomly generates a secret number between **0 and 99**, and the player must guess it.
After each guess, the game will tell you whether your guess was:

* 📉 Too small
* 📈 Too big
* 🎉 Correct

---

## 🚀 How to Run

Make sure you have [Rust](https://www.rust-lang.org/tools/install) installed.
Then, clone the repository and run the project with Cargo:

```bash
git clone https://github.com/G4BR-13-L/the-book-guessing-game.git
cd guessing-game
cargo run
```

---

## 💻 Example Run

```
Guess the number!
Please, input your guess.
50
Too small!
75
Too big!
63
You Win!
```

---

## 🧩 Code Snippet

```rust
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the number!");
    println!("Please, input your guess.");

    let secret_number = rand::rng().random_range(0..100);

    loop {
        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read the line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please, type a number: ");
                continue;
            }
        };

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You Win!");
                break;
            }
        }
    }
}
```

---

## 📚 References

* 📖 [The Rust Programming Language Book — Chapter 2: Guessing Game](https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html)
* 🦀 [Rust Official Website](https://www.rust-lang.org/)

---

✨ Have fun learning Rust!
