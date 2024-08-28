# Memory Ordering

### Atomic

An atomic instruction is an indivisible instruction, happens in a single block where don't have CPU time space to
another instruction make an action. With an atomic instruction we can be sure that we'll have success or an error
without the possibility of a false negative (maybe will fail it's not possible)

- `compare_enchange` function

Execute a block of load/store instructions in atomic way without the possbility to change the value between the
operation. Used outside a loop, e.g:

```rust
let a = AtomicBool::new(0);

// If current value in variable 'a' is equals 0 then add 1 (one) on the current value of 'a'
let _ = a.compare_exchange(0, a + 1, Ordering::Relaxed, Ordering::Relaxed);
```

- `compare_exchange_weak` function

Compare exchange weak has the same behavior of the compare exchange function with the only difference that is most
common used in a loop

```rust
let a = AtomicBool::new(0);

// While the value on 'a' is different of zero spin (wait)
while atomic.compare_exchange_weak(0, 1, Ordering::Relaxed, Ordering::Relaxed).is_err() {}
```

### Ordering

- Relaxed

Have the possibility to another thread to execute any operation between the Relaxed operation, allowing instruction
reorder too

- Acquire/Release

Starts a before-after relationship between instructions not allowing the compiler to reorder the instructions between
operations

- AcqRel

`load` atomic call use Acquire ordering and `store` atomic call use Release ordering. Most commom on a single statement
operation (load/store) happens on the same operation without middle operations ("oneline" calls)

- SeqCst

Starts a before-after relationship ONLY ON operations that have the same ordering. The relationship is visible between
all threads

@@@: MESI protocol
