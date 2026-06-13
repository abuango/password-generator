# Password Generator

[This project is a training demo]

A single-page web app that generates random passwords and estimates how long they would take to brute-force crack. Everything lives in [index.html](index.html) — HTML, CSS, and JavaScript in one file, with no build step or dependencies.

## What it does

The page shows two side-by-side cards:

### 1. Password Generator

- **Length** — number of characters in the generated password (input ranges 4–20, defaults to 24).
- **Include Uppercase** — adds `A–Z` to the character pool.
- **Include Numbers** — adds `0–9` to the character pool.
- **Include Symbols** — adds a set of 18 symbols (`!@#$%^&*(){}[]=<>/,.`) to the character pool.

Lowercase letters are always included. Clicking **Generate Password** builds a new password by randomly picking one of the enabled character types for each position.

### 2. Time to Crack

After each generation (and on page load), the app estimates how resistant the password is to a brute-force attack:

- **Character set** — the size of the character pool inferred from the password (lowercase = 26, uppercase = 26, digits = 10, symbols = 20).
- **Combinations** — the total keyspace, calculated as `charsetSize ^ length`.
- **Time to crack** — assumes an attacker guessing **10 billion (1e10) passwords per second** and needing to search, on average, half the keyspace. The result is formatted into a human-readable duration (seconds, minutes, hours, days, or years).

## How to run it

Open [index.html](index.html) in any web browser — no server or installation required.

## Notes / caveats

- Passwords are generated with `Math.random()`, which is **not cryptographically secure**. This is a demo/educational tool, not a production password manager.
- The crack-time figures are rough estimates: they assume a single fixed guess rate and pure brute force (no dictionary or smarter attacks).
- The length input is capped at 20 in the UI, but the field defaults to 24; the estimate uses whatever value is actually entered.
