# similar

[![Build Status](https://github.com/mitsuhiko/similar/workflows/Tests/badge.svg?branch=main)](https://github.com/mitsuhiko/similar/actions?query=workflow%3ATests)
[![Crates.io](https://img.shields.io/crates/d/similar.svg)](https://crates.io/crates/similar)
[![License](https://img.shields.io/github/license/mitsuhiko/similar)](https://github.com/mitsuhiko/similar/blob/main/LICENSE)
[![Documentation](https://docs.rs/similar/badge.svg)](https://docs.rs/similar)

Similar is a dependency free crate for Rust that implements different diffing
algorithms and high level interfaces for it.  It is based on the [pijul](https://pijul.org/)
implementation of the Myer's and Patience algorithms and inherits some ideas
from there.

```rust
use similar::text::{ChangeTag, TextDiff};

fn main() {
    let diff = TextDiff::from_lines(
        "Hello World\nThis is the second line.\nThis is the third.",
        "Hallo Welt\nThis is the second line.\nThis is life.\nMoar and more",
    );

    for op in diff.ops() {
        for change in diff.iter_changes(op) {
            let sign = match change.tag() {
                ChangeTag::Delete => "-",
                ChangeTag::Insert => "+",
                ChangeTag::Equal => " ",
            };
            print!("{}{}", sign, change);
        }
    }
}
```

## What's in the box?

* Myer's diff
* Patience diff
* Line, word, character and grapheme level diffing
* Unified diff generation

## License and Links

- [Documentation](https://docs.rs/similar/)
- [Issue Tracker](https://github.com/mitsuhiko/similar/issues)
- [Examples](https://github.com/mitsuhiko/similar/tree/main/examples)
- License: [Apache-2.0](https://github.com/mitsuhiko/similar/blob/main/LICENSE)

