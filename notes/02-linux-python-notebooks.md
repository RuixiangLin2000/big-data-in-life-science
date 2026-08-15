# Linux、Python 与 Notebook（Linux, Python, and Notebooks）

## Linux 基础（Linux essentials）

Shell 为文件导航、运行工具和组合分析步骤提供了可编程接口。（The shell provides a programmable interface for navigating files, running tools, and composing analysis steps.）

### 导航与文件操作（Navigation and file operations）

```bash
pwd
ls -lah
cd path/to/project
mkdir results
cp input.txt results/
mv old.txt new.txt
rm unwanted.txt
```

绝对路径适合明确的自动化流程，相对路径适合可移植的项目结构；除非确定存在恢复机制，否则应把删除视为不可逆操作。（Use absolute paths for unambiguous automation and relative paths for portable project layouts. Treat deletion as irreversible unless a recovery mechanism is known.）

### 查看与搜索（Reading and searching）

```bash
head -n 20 file.txt
tail -n 20 file.txt
less file.txt
grep -n "pattern" file.txt
find . -name "*.csv"
```

### 管道与重定向（Pipes and redirection）

```bash
command > output.txt
command 2> errors.txt
command_a | command_b
```

管道可以把小程序组合成工作流；自动化作业中应分开标准输出和标准错误。（Pipes let small programs form a workflow. Keep standard output and error separate in automated jobs.）

### 权限与归档（Permissions and archives）

- 读、写和执行权限分别作用于所有者、用户组和其他用户。（Read, write, and execute permissions apply to owner, group, and others.）
- `chmod` 用于修改权限。（`chmod` changes permissions.）
- `tar` 用于打包目录树，gzip 常用于压缩归档。（`tar` packages directory trees; gzip commonly compresses the archive.）
- 符号链接指向已有路径，目标移动后可能失效。（Symbolic links point to existing paths and can break when targets move.）

## Python 基础（Python foundations）

Python 可用于数据处理、脚本、科学计算库和工作流连接。相比冗长且依赖隐藏状态的脚本，应优先使用小型函数、明确输入输出和环境文件。（Python is used for data manipulation, scripting, scientific libraries, and workflow glue. Prefer small functions, explicit inputs/outputs, and environment files over long stateful scripts.）

## Jupyter Notebook（Jupyter notebooks）

Notebook 把文本、代码、输出和图形结合起来，适合探索和教学，但执行顺序可能隐藏状态。（Notebooks combine text, code, output, and figures. They are useful for exploration and teaching, but execution order can hide state.）

良好实践（Good practice）：

- 分享前重启内核并运行所有单元。（Restart the kernel and run all cells before sharing.）
- 将可复用逻辑移到模块或脚本中。（Move reusable logic into modules or scripts.）
- 记录软件包版本和随机种子。（Record package versions and random seeds.）
- 不要在单元格中保存密码、令牌、私人路径或可识别数据。（Do not store passwords, tokens, personal paths, or identifiable data in cells.）
- 分离原始数据、派生数据和展示输出。（Separate raw data, derived data, and presentation output.）
