# Examples

## Basic Usage

Defining flags with auto-incrementing powers of two or explicit overrides, and manipulating them using `set!`, `contains?`, and `toggle!`:

```clojure
(use BitFlags)

; Auto-incrementing flags: Read (1), Write (2), Execute (4)
; Explicit override flag: Admin (32)
(bitflags [Read Write (Admin 32) Execute])

(defn main []
  (let [f (BitFlags.new 0)]
    (do
      (BitFlags.set! &f Read)
      (BitFlags.set! &f Write)
      (IO.println &(str (BitFlags.contains? &f Read))) ; true
      (BitFlags.toggle! &f Admin)
      (IO.println &(str (BitFlags.to-int &f)))))) ; 35
```
