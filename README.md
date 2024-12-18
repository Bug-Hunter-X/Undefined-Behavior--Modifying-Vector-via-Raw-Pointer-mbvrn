# Rust Undefined Behavior Example

This repository demonstrates a common source of undefined behavior in Rust: modifying a vector through a raw pointer after potentially changing its capacity.  The code in `bug.rs` directly manipulates the vector's underlying memory, leading to unpredictable results. The solution (`bugSolution.rs`) showcases safer alternatives to achieve the same outcome.

## How to Reproduce
1. Clone the repository.
2. Navigate to the repository's directory.
3. Run `cargo run` (for the buggy code) and `cargo run --bin bugSolution` (for the solution).

## How it Works
The original code uses `as_mut_ptr()` to obtain a raw pointer to the vector's data. Then, it directly modifies the value at this pointer using unsafe code. This is inherently dangerous as the vector's internal structure might change (e.g., reallocation), invalidating the pointer.  The corrected version avoids this by employing safe Rust methods.