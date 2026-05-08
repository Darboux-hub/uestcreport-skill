# UESTCreport Skill

## 中文说明

`uestcreport` 是一个面向 AI 编程代理的 Agent Skill，用于在任意项目中快速创建、维护和编译电子科技大学研究生课程报告模板。它基于 ThesisUESTC 的 LaTeX 模板文件精简而来，保留 XeLaTeX、中文排版、参考文献、封面字段和 UESTC 标志等核心能力。

本仓库的根目录就是 skill 根目录，可以被 Claude Code 和 Codex 直接克隆使用。

### 支持的代理

- Claude Code
- Codex

### 安装

#### Claude Code

```bash
git clone https://github.com/Darboux-hub/uestcreport-skill.git ~/.claude/skills/uestcreport
```

#### Codex

```bash
git clone https://github.com/Darboux-hub/uestcreport-skill.git ~/.agents/skills/uestcreport
```

#### 本地 Codex Desktop

如果你已经在本机使用当前目录：

```text
C:\Users\Administrator\.codex\skills\uestcreport
```

可以继续保持这个路径不变。该目录已经可以作为 Git 工作树维护，后续直接在当前目录中更新即可。

### 使用示例

在任意目标项目中运行：

```bash
python scripts/create_report.py --output <target-dir>
```

只复制模板、不立即编译：

```bash
python scripts/create_report.py --output <target-dir> --no-compile
```

如果目标目录已有同名模板文件，脚本默认拒绝覆盖。确认要替换时再使用：

```bash
python scripts/create_report.py --output <target-dir> --force
```

### 更新

进入已克隆的 skill 目录后运行：

```bash
git pull
```

### 维护

- 默认分支：`main`
- 首个版本标签：`v0.1.0`
- 更新流程：修改 skill 文件，验证，提交，推送，并在需要时创建新的版本标签。

### 许可与归属

本仓库按 LaTeX Project Public License v1.3c 分发，SPDX 标识为 `LPPL-1.3c`。

`assets/template/thesis-uestc.cls` 和 `assets/template/thesis-uestc.bst` 派生自 ThesisUESTC，原文件版权归 Wen Wang 所有，并保留原 LPPL 许可头。UESTC 标志文件仅用于课程报告模板排版，请按学校标识规范使用。

完整 LPPL 许可文本见：<https://www.latex-project.org/lppl.txt>

---

## English

`uestcreport` is an Agent Skill for AI coding agents. It creates, maintains, and compiles a lightweight University of Electronic Science and Technology of China graduate course report template in any project. The bundled LaTeX template is derived from ThesisUESTC and keeps the core XeLaTeX workflow, Chinese typesetting, bibliography support, cover fields, and UESTC logo placement.

The repository root is the skill root, so Claude Code and Codex can clone it directly into their skills directories.

### Supported Agents

- Claude Code
- Codex

### Installation

#### Claude Code

```bash
git clone https://github.com/Darboux-hub/uestcreport-skill.git ~/.claude/skills/uestcreport
```

#### Codex

```bash
git clone https://github.com/Darboux-hub/uestcreport-skill.git ~/.agents/skills/uestcreport
```

#### Local Codex Desktop

If you already use this local path:

```text
C:\Users\Administrator\.codex\skills\uestcreport
```

you can keep it unchanged. This directory can now be maintained directly as a Git working tree.

### Usage

Run this from the cloned skill directory or reference the script by absolute path:

```bash
python scripts/create_report.py --output <target-dir>
```

Copy the template without compiling:

```bash
python scripts/create_report.py --output <target-dir> --no-compile
```

The script refuses to overwrite existing template files by default. Use `--force` only when replacement is intentional:

```bash
python scripts/create_report.py --output <target-dir> --force
```

### Update

Enter the cloned skill directory and run:

```bash
git pull
```

### Maintenance

- Default branch: `main`
- Initial release tag: `v0.1.0`
- Update flow: edit skill files, validate, commit, push, and tag releases when useful.

### License And Attribution

This repository is distributed under the LaTeX Project Public License v1.3c, SPDX identifier `LPPL-1.3c`.

`assets/template/thesis-uestc.cls` and `assets/template/thesis-uestc.bst` are derived from ThesisUESTC. The original file copyright belongs to Wen Wang and the original LPPL notices are preserved. The UESTC logo asset is included only for course report template layout; use it according to the university's identity rules.

Full LPPL text: <https://www.latex-project.org/lppl.txt>
