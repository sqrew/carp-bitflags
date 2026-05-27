# carp-bitflags

A robust, type-safe bitflags library for the [Carp language](https://github.com/carp-lang/Carp).

This module provides an idiomatic way to manage sets of bitmask flags using integer wrappers.

## Features

- **Type-Safe Wrappers**: Encapsulate raw integers into meaningful flag types.
- **Precise Semantics**: Distinguishes between `contains?` (all) and `intersects?` (any).
- **Full Set Logic**: Support for `union`, `intersection`, `difference`, `symmetric-difference`, and `subset?`.
- **Fluent API**: Set, unset, toggle, and check flags with ease.
- **Functional Support**: `with` and `without` for non-mutable compositions.
- **Zero Overhead**: Compiles down to standard C bitwise operations.
- **Hybrid Power-Macro**: Define flags with auto-incrementing powers of two or explicit `(Flag Value)` overrides.

## Design Philosophy

The BitFlags module is designed for performance and clarity:

1. **Explicit Semantics**: Distinguishes between "setting a flag" and "bitwise ORing" two flag sets.
2. **Safety Layering**: Provides safe inspection and checked mutation.
3. **Systems Friendly**: Perfect for hardware registers, state machines, and API options.

## Installation

Add this to your project by loading `bitflags.carp`.

```clojure
(load "path/to/carp-bitflags/bitflags.carp")
(use BitFlags)
```

## Usage

```clojure
(use BitFlags)

(bitflags [Read Write (Admin 32) Execute]) ; 1, 2, 32, 4

(let [f (BitFlags.new 0)]
  (do
    (BitFlags.set! &f Read)
    (BitFlags.set! &f Write)
    (IO.println &(str (BitFlags.contains? &f Read))) ; true
    (BitFlags.toggle! &f Admin)
    (IO.println &(str (BitFlags.to-int &f))))) ; 35
```

## Running Tests

```bash
carp -x test/bitflags_test.carp
```

## License

MIT
