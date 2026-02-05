Various reports made on the linux kernel, commit
`f14faaf3a1fb3b9e4cf2e56269711fb85fba9458`.

The mentality for which functions to put in `notable.json` and `ignore.json`
is roughly as follows: `notable.json` is meant for functions which ignoring
the return value is more likely to be an error, whereas `ignore.json` is for
functions which returning the return value is not likely to cause an error. An
example of a `notable.json` function would be one which performs some operation
and returns an error code. An example of an `ignore.json` function is a setter
which returns the set value on returning.

To set up, run in the Linux repo:

```
$ make LLVM=1 defconfig
$ make LLVM=1
$ ./scripts/clang-tools/gen_compile_commands.py
```

## Notes

### `__must_check`

Linux has a `__must_check` macro which labels certain function returns as
"must be checked" and errors if the return value is ignored. Our analysis looks
at all functions, not just these.
