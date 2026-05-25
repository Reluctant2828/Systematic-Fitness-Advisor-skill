# 系统健身-skill
# System Fitness Advisor.skill

> 「不只是生成训练计划，而是把系统健身逻辑变成可复用的 AI Skill」

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Agent Skill](https://img.shields.io/badge/Agent-Skill-purple.svg)
![Fitness Knowledge Base](https://img.shields.io/badge/Fitness-Knowledge_Base-green.svg)
![Status](https://img.shields.io/badge/Status-Building-orange.svg)

System Fitness Advisor 是一个系统化健身 AI Skill。

它根据用户的身体数据、训练目标、训练经验、器械条件、时间安排、伤病限制和恢复状态，结合内置训练知识库与动作库，生成安全、可执行、可进阶的健身建议。

它不是简单地给你一张训练表。

它要做的是：

- 采集用户数据
- 判断训练目标
- 进行基础风险筛查
- 调用训练知识库
- 调用动作库
- 生成训练计划
- 给出 RPE / RM / 组间歇规则
- 设置渐进超负荷
- 设置疲劳管理和调整规则

最终目标是：  
把系统健身教练的训练逻辑，成一个可以被 AI 调用的 Skill。

---

## 效果示例

```text
用户 ❯ 我 175cm，75kg，训练半年，想增肌，每周能练 4 天，有健身房，肩膀偶尔不舒服，帮我安排训练。

System Fitness Advisor ❯

先判断目标：
你的主要目标是增肌，同时需要兼顾肩部稳定和动作安全。

不建议直接上高容量六分化。
更适合使用循环三分化或上肢/下肢结合结构。

推荐方案：
第 1 天：推
第 2 天：拉
第 3 天：休息
第 4 天：腿
第 5 天：推
第 6 天：休息
第 7 天：拉或休息

推日会降低高风险过顶推举比例，
优先使用器械推胸、上斜哑铃卧推、绳索侧平举、绳索下压。

肩部不适时：
不直接追求大重量卧推。
先控制 RPE 7–8，观察疼痛反馈。
如果疼痛超过 3/10，需要替换动作或咨询专业人士。
