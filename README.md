# 自由职业采购需求筛选

[新手逐步使用指南](USER_GUIDE.md) · [用途与适用人群介绍](INTRODUCTION.md)

`freelance-marketplace-buyer-pipeline` · 独立技能仓库 · MIT

适合：找外包项目、准备报价的个人或小团队

## 解决什么问题

区分正在采购的项目、招聘岗位与普通公司线索，把精力放在值得继续核验的需求上。

## 快速开始

Python 3.10+，标准库，不调用付费接口。

在本仓库根目录运行：

```sh
python scripts/review_leads.py examples/leads.json
```

## 输入与输出

**输入**：leads 数组，字段同示例；采购项目 kind=project_request；accepting_bids 必须是布尔值。不要用招聘岗位冒充可报价外包。

**输出**：离线 JSON 审查表和排除原因。不会报价、发送消息或声明赢单概率。

## 本次完善

原有缺口：原来是经验说明，缺统一输入输出和可复现演示。

已补：新增离线项目导入检查、待报价状态提示、重复识别和预付款请求排除；提供合成示例与测试。

## 当前限制

快照由使用者提供，工具不能证明网页来源或雇主可靠；仍需本人核对平台状态、费用与预算。不会登录、投标或支付。

## 验证与使用注意

```sh
python -m unittest discover -s tests -v
```

测试覆盖被断言的离线行为，不等于真实平台、生产模型或业务效果验证。

示例数据和图片均为合成演示，不是真实客户、交易、销量或模型成绩。不要提交真实凭据和私有输入。

## 来源与工作记录

由 miaorrr8888-cloud 在 AI 辅助下积累和维护，来源与边界见 [PROVENANCE.md](PROVENANCE.md)，许可见 [LICENSE](LICENSE)。

[全部独立技能与阶段性工作记录](https://github.com/miaorrr8888-cloud/agent-skills-worklog)

## 第二轮：采购证据复核

新增页面快照与原文摘录匹配、快照哈希和 24 小时时效标记，过期或无原文则 HOLD。

在仓库根目录运行：

```sh
python scripts/review_snapshot.py examples/snapshot.json
```

新增工具的输入字段见脚本参数与 examples/。快照示例采用固定日期，过期后正常返回 HOLD；需要检查新采集的页面时填写真实带时区的采集时间，不要改日期伪装新证据。
