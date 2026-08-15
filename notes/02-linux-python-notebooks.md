# Linux、Python 与 Notebook（Linux, Python, and Notebooks）

## 中文导读（Chinese Guide）

Linux Shell 是导航文件、运行程序和组合分析步骤的基础。需要掌握目录与文件操作、文本查看与搜索、管道、输入输出重定向、权限、归档和符号链接。

Python 适合数据处理、科学计算和自动化。代码应使用明确的输入输出和小型函数，并通过环境文件记录依赖。

Jupyter Notebook 便于探索和展示，但容易隐藏执行状态。分享前应重启内核并从头运行全部单元，把可复用逻辑移入脚本，记录软件版本与随机种子，并移除密码、令牌、私人路径和可识别数据。

---

## 英文原文（Original English）

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
