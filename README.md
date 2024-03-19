# jget

[![Crates.io](https://img.shields.io/crates/v/jget)](https://crates.io/crates/jget)
[![Crates.io](https://img.shields.io/crates/d/jget)](https://crates.io/crates/jget)
[![License](https://img.shields.io/crates/l/jget)](LICENSE)

## Cargo.toml

```toml
[dependencies]
jget = { version="0.1.0", features = ["derive"] }
```

Or

```toml
[dependencies]
jget = { version="0.1.0", features = ["derive"] }
```

## Usage

```rust
use jget::Jget;


#[derive(Debug, Jget)]
pub enum SimpleEnumExample {
    Read {
        #[jget(get_option)]
        value: u8,
    },
    Write {
        #[jget(get_option)]
        value: u8,
        #[jget(get_option)]
        data: u16,
    }
}


fn main() {
    let value = SimpleEnumExample::Read { value: 1 };
    assert_eq!(value.get_value(), Some(1));
    assert_eq!(value.get_data(), None);

    let value = SimpleEnumExample::Write { value: 1, data: 2 };
    assert_eq!(value.get_value(), Some(1));
    assert_eq!(value.get_data(), Some(2));
}
```