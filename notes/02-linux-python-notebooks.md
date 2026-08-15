# Linux, Python, and Notebooks

## Linux essentials

The shell provides a programmable interface for navigating files, running tools, and composing analysis steps.

### Navigation and file operations

```bash
pwd
ls -lah
cd path/to/project
mkdir results
cp input.txt results/
mv old.txt new.txt
rm unwanted.txt
```

Use absolute paths for unambiguous automation and relative paths for portable project layouts. Treat deletion as irreversible unless a recovery mechanism is known.

### Reading and searching

```bash
head -n 20 file.txt
tail -n 20 file.txt
less file.txt
grep -n "pattern" file.txt
find . -name "*.csv"
```

### Pipes and redirection

```bash
command > output.txt
command 2> errors.txt
command_a | command_b
```

Pipes let small programs form a workflow. Keep standard output and error separate in automated jobs.

### Permissions and archives

- Read, write, and execute permissions apply to owner, group, and others.
- `chmod` changes permissions.
- `tar` packages directory trees; gzip commonly compresses the archive.
- Symbolic links point to existing paths and can break when targets move.

## Python foundations

Python is used for data manipulation, scripting, scientific libraries, and workflow glue. Prefer small functions, explicit inputs/outputs, and environment files over long stateful scripts.

## Jupyter notebooks

Notebooks combine text, code, output, and figures. They are useful for exploration and teaching, but execution order can hide state.

Good practice:

- Restart the kernel and run all cells before sharing.
- Move reusable logic into modules or scripts.
- Record package versions and random seeds.
- Do not store passwords, tokens, personal paths, or identifiable data in cells.
- Separate raw data, derived data, and presentation output.
