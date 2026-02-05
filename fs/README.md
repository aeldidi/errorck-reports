This is the report done on some of the filesystems in the linux kernel
mainline.

Some functions set a value in some struct and return the value which they set.
These cases, like the `inode_set_mtime_to_ts` function, are harmless to ignore
the return values for.

both `functions.json` and `ignore.json` here were made by reading `fs.h`. The
report was run on all the `.c` and `.h` files in the `fs/` directory.

Command ran: 

```bash
find ../../fs/ -type f \( -name '*.c' -o -name '*.h' \) -exec python3 ../../../errorck/scripts/run_errorck_analysis.py --errorck ../../../errorck/build/errorck --notable-functions functions.json --ignored-functions ignore.json --compdb ../../compile_commands.json {} +
```
