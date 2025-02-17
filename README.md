# libmambapy-windows-segfaults

See https://github.com/conda/conda-libmamba-solver/issues/334 for details.

Releases are used to distribute patched libmambapy builds with extra debugging.

- 2024-12-19: Original debugging libraries. Will print the stack if segfaults occur.
- 2024-12-20: Same, but with some extra assertions about pointers.
- 2024-12-23: No `ObjTransaction::order` calls. Some pointer assertions.
- 2024-12-24: Check destroyed objects and maybe have a more detailed stack.
- 2025-01-02: Some more fixes for the stack.
- 2025-01-06: Some more logging fixes, potential workaround included.
- 2025-01-16: Same as last one but with some additional C runtime DLLs.
- 2025-01-17: Get some info around `-ObjPool`.
- 2025-01-21: Try to get some more info on those pesky transaction objects.
- 2025-01-22: Leak Transaction objects on purpose. Include custom debug libsolv build.
- 2025-01-30: Two builds, one control and one with a fix. None of the logs anymore. The control one should fail.
- 2025-02-11: Two builds, one control (should segfault) and one with the fix (should not). Built off recent `main` (2.0.6ish). Release builds, no debugging.
  - The fix will defer freeing libsolv's transactions (the workaround) until just after deleting a pool, at the end of the program (fail-safe) or if the function that does the freeing is called explicitly; exposed in the bindings the function that does the freeing of transactions (for later test if necessary), it's called `free_all_deferred_transactions_workaround()` and has no parameters.
- 2025-02-17: Alternative workaround with corrected tree structure
