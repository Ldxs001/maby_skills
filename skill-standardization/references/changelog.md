## [2.103.0] - 2026-08-04

### 修复（引擎自身严重缺陷，refactor 实战暴露）

1. **YAML 折叠块解析丢失（P0）**：`parse_simple_yaml_frontmatter` 忽略 `>`/`|` 折叠块
   及续行，auto-fix 重写 frontmatter 时把 description/trigger 清空。新增折叠块/字面块
   收集与合并逻辑，`_fmt_frontmatter_value` 支持多行还原。修复后 auto-fix 不再抹空内容。
2. **R-10 trigger 字面比较必误报（P0）**：frontmatter 自然语言文本 vs _meta.json 关键词
   数组做 `!=` 比较，语义等价必然报 ERROR。改为语义包含比较（任一方向包含即一致，
   真不一致仍报错）。
3. **C-14 工作流 JSON 路径拼错（P0）**：`basename(dirname(dirname(_skill_dir)))` 多套
   一层 dirname 取到 `.workbuddy` 而非 `skills`，引擎永远找不到 `.structure_workflow.json`
   导致 LLM 确认无效。改为与 `_manual_dir_path` 同源算法。
4. **快照路径分裂 HARD-BLOCK（P1）**：`_clean_stale_state` 删除状态文件但不同步删
   `.fp_snapshot.json` 指纹 → 永久状态不一致。cleanup 现同步删快照条目；`_update_snapshot`
   文件不存在时删条目而非存 null。
5. **C-11 synonyms 歧义覆盖（P1）**：「限制」等章节名被「约束」synonyms 抢匹配导致
   伪逆序。新逻辑：synonyms 值与 section_order 独立项相关时优先用 order 位置。
6. **R-25 fix key 映射错位（P2）**：C-07 误映射 trigger_format（应为 code_block_lang）、
   C-12 细分约束/表格/工作流。

## [2.102.9] - 2026-07-09

### 修复
- **displayName 统一为 kebab-case**：ClawHub/SkillHub 发布的显示名与技能名一致（），废除驼峰格式

## [2.102.8] - 2026-07-09
## [2.102.8] - 2026-07-03

### 修复
- 修复: `structure_checker.py` C-13 索引表检查仅匹配 `references/` 前缀的表格行，漏检 `scripts/` 等非 references 条目。新增 EXTRA 检查：索引表中所有文件路径必须以 `references/` 开头，否则报 WARN

## [2.102.7] - 2026-07-03

### 修复
- 修复: `fix.py` `fix_section_trigger()` 在 auto-fix 生成的触发词前硬加"用户需要"前缀，导致 auto-fix→audit→refix 非收敛循环。改为直接使用采集到的触发词原文（来自脚本 docstring / frontmatter / description），不再前缀"用户需要"

## [2.102.6] - 2026-07-03

## [2.102.5] - 2026-07-03

### 修复
- 修复: `body.json` 在 约束 章节同义词中添加「能力边界」「能力边界与限制」「能力与边界」，使 C-11 不再误报这些常用章节名

## [2.102.4] - 2026-07-03

### 修复
- 修复: `structure_checker.py` R-23 路径解析使用源文件目录而非 skill_dir（`references/` 下的路径应相对 source file 目录解析，而不是从 skill_dir 解析）
- 修复: `fix.py` `fix_section_workflow()` 在 ## 工作流程 已有自定义内容时跳过覆盖（避免每次 refactor --continue 销毁已有的工作流表格和门禁表）

## [2.102.3] - 2026-07-01

### 修复
- 修复: `fix_progressive_index_table()` 在替换索引表时会丢失 SKILL.md 中已有的人工填写内容。新增 `existing_rows` 保留机制：先读取现有表格行内容，仅对新文件调用 STANDARDIZED 或 auto-generate，已有行保持原有 4 列内容不变。
