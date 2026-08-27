# carp-bitflags

A robust, type-safe bitflags library for the [Carp language](https://github.com/carp-lang/Carp).

This module provides an idiomatic way to manage sets of bitmask flags using integer wrappers.

## Features

- **Type-Safe Wrappers**: Encapsulate raw integers into meaningful flag types.
- **Precise Semantics**: Distinguishes between `contains?` (all) and `intersects?` (any).
- **Full Set Logic**: Support for `union`, `intersection`, `difference`, `symmetric-difference`, and `subset?`.
- **Validation Helpers**: Includes `power-of-two?` and `single-bit?` for mask integrity.
- **Fluent API**: Set, unset, toggle, and check flags with ease.
- **Functional Support**: `with` and `without` for non-mutable compositions.
- **Zero Overhead**: Compiles down to standard C bitwise operations.
- **Hybrid Power-Macro**: Define flags with auto-incrementing powers of two or explicit `(Flag Value)` overrides.

## Design Philosophy

The BitFlags module is designed for performance and clarity:

1. **Inspection/Query**: Functions like `contains?`, `intersects?`, and `empty?` return `Bool`.
2. **Mutation**: `set!`, `unset!`, and `toggle!` perform in-place bitwise modifications.
3. **Functional Composition**: `with`, `union`, etc., return new `BitFlags` instances.
4. **Macro Integrity**: The `bitflags` macro uses a pure syntax-transformation approach for maximum compiler compatibility.

## Installation

Add this to your project by loading `bitflags.carp`.

```clojure
(load "path/to/carp-bitflags/bitflags.carp")
(use BitFlags)
```

## Examples

See [examples.md](examples.md) for usage examples.

## Running Tests

```bash
carp -x test/bitflags_test.carp
```

## License

MIT
