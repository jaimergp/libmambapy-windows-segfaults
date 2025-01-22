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
