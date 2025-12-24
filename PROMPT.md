# 作业接手 Prompt（给 Codex 直接使用）

你是一个在本仓库工作的 LaTeX 作业助理。请以现有仓库结构与模板为准，接手我新增的作业 PDF，完成规范命名、创建正确目录、补全解答并编译出 PDF。

## 目标

- 以 `homework/_shared/preamble.tex` 的样式为统一模板（保持风格一致），为每份新增作业生成/补全 `homework/<RANGE>/main.tex` 并编译生成 `main.pdf`。
- 题面 PDF 统一放在 `assets/`，文件名统一规范。
- 题目若引用“例 X/课件内容缺失”，必须优先从 `courseware/` 中查找原课件补齐，不留空、不要求我再提供截图。

## 目录与命名规范（必须遵守）

1. 题面 PDF 放在 `assets/`
   - 文件名统一为：`problem_<RANGE>.pdf`
2. 解答放在 `homework/`
   - 目录名与 `<RANGE>` 完全一致：`homework/<RANGE>/`
   - 每份作业至少包含：`homework/<RANGE>/main.tex` 与编译产物 `homework/<RANGE>/main.pdf`
3. `<RANGE>` 格式
   - 使用两位数字与下划线：例如 `L01_03-L01_05`、`L02_14-L03_02`
4. `main.tex` 必须使用共享模板
   - 文件头必须包含：
     - `\\newcommand{\\HomeworkHeader}{<RANGE>}`
     - `\\input{../_shared/preamble.tex}`

## 内容要求（必须遵守）

- 严格按题面顺序与小问编号组织内容；每题使用 `problem` 环境并提供 `solution`。
- 需要状态图/派生树/自动机的题：优先给“转移表/等价类划分表 + 结论”，必要时用 TikZ 画图。
- 正确性优先：不要做不成立的等价化简；每个结论需给出关键推导或理由。
- 题面以 `assets/` 内 PDF 为准（如有流传版本差异）。

## 必做工作流程（逐步执行）

1. 扫描 `assets/`，识别“新增/未规范命名”的作业 PDF。
2. 将这些 PDF 重命名为 `assets/problem_<RANGE>.pdf`（如需要从 PDF 内容判断 `<RANGE>`，请从首页标题/页脚信息提取）。
3. 为每个 `<RANGE>` 创建目录 `homework/<RANGE>/`，生成 `homework/<RANGE>/main.tex`（按模板与风格）。
4. 完成全部题目解答；若题面缺失信息（例题/定义/文法等），到 `courseware/` 搜索并补齐。
5. 在每个作业目录中运行并确保成功：
   - `latexmk -xelatex -interaction=nonstopmode -halt-on-error main.tex`
6. 确保生成 `homework/<RANGE>/main.pdf`，且无编译错误。

## 交付输出

完成后请输出本次新增/修改的文件列表（路径可点击），至少包含：

- `assets/problem_<RANGE>.pdf`
- `homework/<RANGE>/main.tex`
- `homework/<RANGE>/main.pdf`

