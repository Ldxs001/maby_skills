<!--
SPDX-License-Identifier: MIT
Copyright (c) 2026 wUwproject
-->

# Maby Skills — 技能仓库

> wUwproject 开发的重型技能（Skill）集合。MIT License。

## 仓库定位

本仓库独立托管 wUwproject 的技能合集，是 **git-sync 的默认技能同步目标仓库**。2026-08-02 自 `workbuddy-skills` 仓库的 `skills/` 目录独立拆分而来。

**历史提交说明：** 本仓库为全新初始化，不带历史提交。所有历史记录保留于永久存档仓库：

- Gitee: https://gitee.com/wUwproject/workbuddy-skills （`skills/` 目录）
- GitHub: https://github.com/Ldxs001/workbuddy-skills （`skills/` 目录）

## 技能列表

| 技能名 | 说明 |
|--------|------|
| `activity-duration-estimation` | 活动历时估算 + WBS + 项目文档 + 经济效益分析 + 挣值管理 |
| `analysis-toolkit` | 检验检测行业质量控制与数据分析工具箱 |
| `color-toolkit-turn` | 专业颜色工具集 |
| `drawiodo` | draw.io 自动做图 |
| `everything-search-breadmemory` | 本地搜索 + 知识管理 |
| `git-sync` | 全平台统一发布工具 |
| `hug-html` | HTML 组件库 |
| `latex-modular` | LaTeX 模块化组合 |
| `local-rag-builder` | 本地 RAG 搭建 |
| `memory-pet` | 宠物记忆压缩 |
| `novel-weaver` | 结构化小说写作 |
| `round-robin-allocator` | 均匀轮转分配 |
| `semantic-split` | 语义拆分与规划 |
| `simulated-peak-plot` | 模拟峰图生成 |
| `skill-function-test` | 技能场景测试套件 |
| `skill-standardization` | 技能标准化审计引擎 |
| `skill-sub` | 调用链编排 |
| `svg-composer` | SVG 拼接工具 |
| `triphasic-execution` | 三步循环执行框架 |
| `universal-file-ops` | 文件操作与代码质量 |
| `workday-calendar` | 智能周历系统 |

## 目录结构

```
maby_skills/
├── LICENSE                    # MIT License
├── README.md
└── <skill-name>/              # 各技能（含 _meta.json / SKILL.md / scripts/ / references/）
```

## 维护约定

- 本仓库由 **git-sync** 技能自动同步维护（默认技能同步目标）
- 技能版本号从各自 `_meta.json` 读取
- 更新流程：修改 → 双零审计 → bump → git-sync 推送（Gitee / GitHub 双平台）
- 许可证：MIT（所有技能统一）
