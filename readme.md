# 学术论文专业润色 Skill（academic-paper-polish-skill）

> 强约束型专业学术润色能力：面向期刊论文、硕博学位论文，依据 **24 条统一学术写作规范**完成段落/全文润色；严格保留原文数据、公式、符号、结论，仅优化逻辑、句式、术语、数据表述。

## ✨ 项目特色

1. **24 条规则库，可单独迭代**：结构组织 6 条 / 逻辑因果 5 条 / 术语符号 4 条 / 数据验证 7 条 / 公式结果 2 条，每条带正反例，独立文件解耦，新增规则无需改动主流程
2. **五层约束 + 五步 Workflow**：总原则 → 规则库 → 风格基准 → 操作红线 → 数据口径 五层强制约束；准入校验 → 元素拆解 → 分层修正 → 全局复检 → 输出分支 五步闭环流程
3. **数据红线保护**：不修改、不删减、不新增任何数值数据、公式、符号、图表编号、文献引用；冲突数据仅提示不代改（`constraints/forbidden_action.md` 最高优先级）
4. **触发过滤 + 安全拦截**：正反向触发规则独立维护（`meta/trigger_filter.yaml`），代写、降重、编造数据、纯翻译等场景自动拦截
5. **62 条分层样例库**：常规 / 语病 / 边界 / 拦截 四类真实输入输出对，覆盖公式、多符号、中英混排、长试验段落等边界场景
6. **测试回归 + 发布清单**：`test/test_suite.xlsx` 批量用例 + `ops/release_checklist.md` 八层自检，通过率 100% 才可发布，防止迭代退化
7. **场景无限扩展**：可外挂细分领域规范（机械 / 计算机 / 材料专用术语），插入 Workflow 术语标准化环节，不破坏主架构

## 🚀 快速开始

### 方式一：安装为 Reasonix Skill（推荐）
1. 将本仓库克隆或下载到本地
2. 在 Reasonix 中执行 Skill 安装（支持本地文件夹 / URL 两种来源），安装器识别 `SKILL.md` 为入口并保留全部依赖文件
3. 安装后输入 `/academic-paper-polish-skill` 直接调用；对话中出现「论文润色、术语统一、数据表述规范」等触发词时自动启用

### 方式二：手动使用（任意 AI 环境）
把 `core/skill_main.md` 内容作为上下文提供给任意 AI 模型，模型会按 `depend_file` 引导依次加载：

```
core/skill_main.md        → 主 Skill（Trigger / Rules / Workflow / 输出分支）
core/rule_base.md         → 24 条规则库（逐条校验）
core/style_standard.md    → 人称 / 措辞 / 段落模板
constraints/forbidden_action.md → 操作红线（最高优先级）
constraints/data_form_spec.md   → 公式 / 符号 / 数据口径
meta/trigger_filter.yaml  → 正反向触发判定
```

### 使用流程
1. **触发判定**：正向命中（论文润色 / 学术段落优化 / 术语统一 / 数据表述规范）启用；反向命中（代写 / 降重 / 编造数据 / 纯翻译）拦截
2. **润色执行**：五步 Workflow（准入校验 → 元素拆解 → 分层修正 → 全局复检 → 输出分支）
3. **输出形态**：默认只输出润色后文本；要求批注时输出「文本 + 规则编号标注」；多章节长文按原分段输出

## 📁 目录结构

```Plain Text
skill_academic_polish/
├── meta/
│   ├── skill_meta.yaml          # 全局元信息、版本、依赖、能力标签
│   └── trigger_filter.yaml      # 正向/反向触发关键词、意图规则库
├── core/
│   ├── skill_main.md            # 主Skill主体（Meta+Trigger+Rules+Workflow）
│   ├── rule_base.md             # 独立24条学术润色规则库（解耦，单独更新）
│   └── style_standard.md        # 学术风格基准、人称、句式模板
├── constraints/
│   ├── forbidden_action.md      # 禁止行为、修改铁律、安全约束
│   └── data_form_spec.md        # 公式/符号/数据统一口径规范
├── examples/
│   ├── normal_case.md           # 常规段落润色样例：引言/方法/结果/结论（16条）
│   ├── error_case.md            # 典型语病、违规句式修正样例（16条）
│   ├── edge_case.md             # 边界场景：长公式、多符号、混合中英文（14条）
│   └── reject_case.md           # 不触发润色的拦截案例（16条）
├── test/
│   ├── test_suite.xlsx          # 批量测试用例（输入+预期输出+校验规则编号）
│   └── test_report_template.md  # 迭代测试报告模板
├── ops/
│   ├── iteration_record.md      # 迭代更新日志（版本、修改点、新增规则、修复问题）
│   └── release_checklist.md     # 上线发布自检清单
├── docs/
│   └── README.md                # 捐赠收款码替换说明
└── readme.md                    # 项目说明、使用方式、迭代流程指引
```

## 🔄 迭代机制（持续演进）

```
需求收集 → 修改对应分层文件 → 批量测试回归 → 记录迭代日志 → 发布自检 → 发布
```

| 迭代场景 | 只需修改 | 无需改动 |
|---|---|---|
| 新增写作规范 | `core/rule_base.md`（补正反例） | 主 Workflow |
| 优化触发过滤 | `meta/trigger_filter.yaml` | 主流程 |
| 补充细分场景 | `examples/` 新增文件 | 规则 |
| 修复润色漏洞 | Workflow 分层步骤 + 边界用例 | 规则库 |

- **版本规则**：主版本.功能迭代.补丁修复（如 V1.1.0）；底层架构改动升主版本，新增大类规则升功能迭代，修正漏洞/补充样例升补丁
- **强制记录**：每次更新填写 `ops/iteration_record.md`（变更文件、新增规则、测试结果、遗留问题），支持版本追溯与回滚
- **发布强校验**：`ops/release_checklist.md` 八层自检 + `test/test_suite.xlsx` 全量用例通过率 100% 才可发布

## 🛡️ 安全与边界

- 拒绝代写、论文降重、编造实验数据、生成完整论文
- 拒绝虚构试验条件、补充原文不存在的对比方案
- 数据异常仅提示，不擅自修改；润色前后数值/公式/引用零改动

## 📜 许可证

[MIT](LICENSE) © 2026 paper-polish-team

## 💖 捐赠支持

如果本项目对你的论文写作有帮助，欢迎打赏支持持续迭代：

<!-- 将收款码图片保存为 docs/donate-qr.png 后，取消下一行注释即可展示 -->
<!-- ![捐赠收款码](docs/donate-qr.png) -->

> 替换方法见 [docs/README.md](docs/README.md)。
