# 自由职业采购项目信息整理：用户使用指南

## 它能帮你做什么

按输入字段检查采购项目记录，排除部分不相关类别，提示是否缺少采购状态和证据。

## 适合谁

准备研究外包项目并报价的自由职业者或小团队。

## 具体解决什么问题

项目链接、采购状态、预算与证据没整理好，就容易把招聘、自我推广或过期项目当成可报价机会。

**不适合这些目标：**自动找单、自动识别雇主是否可靠、自动投标、自动付款或保证赢单。

## 下载与准备

- [打开独立仓库](https://github.com/miaorrr8888-cloud/freelance-marketplace-buyer-pipeline)
- [直接下载源码ZIP](https://github.com/miaorrr8888-cloud/freelance-marketplace-buyer-pipeline/archive/refs/heads/main.zip)

也可在仓库页面点 Code → Download ZIP。解压后打开包含 SKILL.md、README.md、USER_GUIDE.md 的那层文件夹。不要停在外层目录或只复制一个脚本。

建议使用Windows电脑和Python 3.12；这是本次验证环境。先在该文件夹打开PowerShell，再执行：

```powershell
python --version
python -m venv .venv
.\.venv\Scripts\python.exe --version
```

这里直接使用虚拟环境里的Python，不需要运行激活脚本或修改系统执行策略。安装步骤及其他系统说明见[通用安装说明](https://github.com/miaorrr8888-cloud/agent-skills-worklog/blob/main/INSTALLATION.md)。

本指南的基础示例只用Python标准库，无需安装第三方Python包。

## 第一次使用：先跑自带示例

自带采购请求示例进入待人工核验；自我推广示例被排除。把 accepting_bids 改为false后应提示状态未确认。

```powershell
.\.venv\Scripts\python.exe scripts/review_leads.py examples/leads.json
```

## 结果怎么看

结果输出每条记录状态和原因。NEEDS_HUMAN_VERIFICATION只表示字段满足进一步核验条件，不表示项目真实开放或雇主已验证。

## 换成自己的资料

leads数组，采购项目kind为project_request；accepting_bids填写布尔值true/false，不是字符串。保留项目URL和原文摘录。

先人工核对平台页面，把明确观察到的信息填入记录；缺预算保留null。需要内容证据时按README使用页面快照检查，并留意过期状态。

## 不想手动敲命令：给AI助手的任务

以下任务适用于能读取所选目录、执行本地命令的助手。WorkBuddy需要先确认当前版本的权限与技能启用状态；本项目未完成WorkBuddy实际导入验收。

```text
请先读取我选定文件夹中的 SKILL.md 和 USER_GUIDE.md，只在该项目范围内处理。
只审查自带采购项目样例，解释待人工核验、排除和缺失项。不要登录平台、投标、发送消息或购买任何额度。随后告诉我怎样用自己核对过的项目记录替换样例。
缺少依赖时先说明用途，优先放进本项目虚拟环境；不要读取其他目录中的密码、密钥或浏览器登录数据。
```

## 常见问题

**true被写成"true"仍提示不确认**

JSON布尔值不能加引号；字符串不是已确认布尔状态。

**预算没有填写会怎样**

保留未知，不估算收入或补一个看似合理的数字；回平台核对。

**找不到文件或脚本**

确认终端当前目录就是包含SKILL.md的技能根目录；路径含空格时加双引号。输出目录已存在时换新名字，不覆盖已有结果。

## 当前能力边界

开放状态、雇主可靠性、费用仍需在平台确认。程序不登录、不报价、不购买额度、不联系客户。

## 验证范围

本指南示例已在Windows独立副本中运行复核，见[命令复核结果](https://github.com/miaorrr8888-cloud/agent-skills-worklog/blob/main/USER_GUIDES_VERIFICATION.md)。已有回归测试只覆盖被测试行为，不证明真实业务结果。WorkBuddy实际运行、手机端使用和所有系统版本均不在本次已验证范围内。

许可证和素材来源分别见 [LICENSE](LICENSE)、[PROVENANCE.md](PROVENANCE.md)。
