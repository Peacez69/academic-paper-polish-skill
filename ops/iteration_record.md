# 学术润色Skill 迭代更新记录

> 使用说明：每次版本更新强制填写一节；支持回滚（按版本号找回历史文件快照）。
> 版本规则：主版本.功能迭代.补丁修复。

---

## 版本号：V1.1.0
更新日期：2026-08-12
更新人：paper-polish-team
变更类型：规则新增 / Workflow步骤扩充 / 样例补充

### 变更详情
1. 修改文件路径：
   - core/rule_base.md：新增规则 25「文本层级与文体角色识别适配」（第六类）
   - core/skill_main.md：Step2 扩展为「文本元素拆解、层级与角色识别」；Step3 新增第 0 步「层级×角色策略选择」；Step4 新增第 6 项适配复检；description 更新为 25 条规范；Examples 新增句子级/段落级识别案例
   - core/style_standard.md：新增「六、层级×角色识别矩阵」
   - meta/skill_meta.yaml：版本升至 V1.1.0
   - 一致性修复（V1.1.0 收尾）：core/skill_main.md version V1.0.0 → V1.1.0；core/rule_base.md 标题、SKILL.md、readme.md、constraints/forbidden_action.md、ops/release_checklist.md、examples/normal_case.md 规则数引用 24 → 25 条对齐
2. 新增/调整内容：
   - 自动识别四层级（篇章/小节/段落/句子）× 四角色（引言介绍/方法/结果陈述/结论）
   - 每层级×角色配独立处理策略；句子级仅句内优化，不改变句子边界
3. 修复问题（如有）：无

### 配套补充动作
1. 补充测试用例：test/test_suite.xlsx 新增 2 条（层级识别 0013/0014），全量用例 14 条
2. 新增样例：core/skill_main.md Examples 补 2 条识别案例，examples/normal_case.md 补 4 条
3. 规则编号变动：core/rule_base.md 新增第 25 条，1~24 编号不变

### 测试结果
批量用例通过率：100%（14/14，含新增层级识别用例 0013/0014 回归）
测试报告：test/test_report_V1.1.0.md
遗留待优化点：
- 角色识别依赖信号词，多角色混合段落（如结果+讨论）按主导角色处理，细分策略待后续迭代

### 发布记录
- 发布日期：2026-08-12
- 发布包：academic-paper-polish-skill-v1.1.0.zip（含 test/test_report_V1.1.0.md）
- 发布自检：ops/release_checklist.md 全部 ☑ 通过，正式发布 V1.1.0

---

## 版本号：V1.0.0
更新日期：2026-08-12
更新人：paper-polish-team
变更类型：项目初始化 / 首次发布

### 变更详情
1. 修改文件路径：全部文件首次创建
2. 新增/调整内容：
   - core/skill_main.md：主 Skill（Meta+Trigger+五层Rules+五步Workflow+示例）
   - core/rule_base.md：24 条学术写作规则（结构6 / 逻辑5 / 术语4 / 数据7 / 公式2），含正反例
   - core/style_standard.md：人称、措辞、段落结构模板、英文辅助规范
   - constraints/forbidden_action.md：操作红线 + 冲突优先级
   - constraints/data_form_spec.md：公式/符号/数据统一口径
   - meta/：skill_meta.yaml + trigger_filter.yaml（正反向触发）
   - examples/：normal 16 条、error 16 条、edge 14 条、reject 16 条
   - test/：test_suite.xlsx（12 条基线用例）+ test_report_template.md
   - ops/：iteration_record.md + release_checklist.md
3. 修复问题（如有）：无（首次发布）

### 配套补充动作
1. 补充测试用例：test/test_suite.xlsx 首批 12 条基线用例
2. 新增样例：examples/ 四类样例库共 62 条
3. 规则编号变动：无（首次建立 1~24 稳定编号）

### 测试结果
批量用例通过率：待首次全量执行（预期 100%）
遗留待优化点：
- rule_base.md 24 条规则为按分类框架整理的标准规范，如团队已有历史规则原文，可整体替换并保持编号映射
- 细分领域（机械/计算机/材料）术语规范待后续外挂补充
