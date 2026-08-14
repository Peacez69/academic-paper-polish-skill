---
name: academic-paper-polish-skill
description: 通用学术论文专业润色能力：对期刊/学位论文段落与全文做标准化润色，遵循24条学术写作规范，优化逻辑、术语、数据表述，不篡改数据、公式与核心观点。触发词：论文润色、学术段落优化、术语统一、数据表述规范、试验描述规范。
---

# 学术论文专业润色 Skill（标准包装入口）

本文件是 Reasonix 标准安装入口（SKILL.md）；执行主体与全部规则位于同目录文件包中，按下列顺序加载。

## 加载顺序
1. `core/skill_main.md` —— 主 Skill：Meta + Trigger + 五层 Rules + 五步 Workflow + 示例，本能力的执行主体
2. `core/rule_base.md` —— 24 条学术写作规则库（结构/逻辑/术语/数据/公式），润色时逐条校验
3. `core/style_standard.md` —— 人称统一、措辞约束、段落结构模板
4. `constraints/forbidden_action.md` —— 操作红线，优先级高于一切优化逻辑
5. `constraints/data_form_spec.md` —— 公式/符号/数据统一口径细则
6. `meta/trigger_filter.yaml` —— 正反向触发判定（命中反向即拦截）

## 执行要点
- 准入：按 `meta/trigger_filter.yaml` 判定；命中反向排除（代写/降重/编造数据/纯翻译等）立即终止，切换通用对话
- 红线：不得修改、删减、新增任何数值数据、公式、符号、图表编号、文献引用；冲突数据仅提示
- 输出：按 `core/skill_main.md` Step5 分支组装（纯文本 / 批注标注 / 多章节分段）
- 样例：`examples/` 下 normal（常规）/ error（语病）/ edge（边界）/ reject（拦截）四类可对照参考

## 迭代
规则/触发/样例分层解耦：改 `core/rule_base.md`、`meta/trigger_filter.yaml`、`examples/` 即可，无需改动主流程；每次迭代后跑 `test/test_suite.xlsx` 并填写 `ops/iteration_record.md`。
