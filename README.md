# recomp-coach

一个 Claude **Agent Skill**，将 Claude 转变为一个确定性状态机教练，管理一套 **5:2 轻断食 × 碳水循环** 身体重组方案。面向一位健康成年男性（179 cm，~68 kg，~20% 体脂），目标是在保留瘦体重的前提下将体脂降至 **13–14%**。

## 核心功能（三步流水线）

每次用户提交训练/饮食日志时，skill 会严格按以下顺序执行：

1. **解析（Parse）** — 将日志提取为 JSON，与 `schema/daily_log.schema.json` 校验。
2. **诊断（Diagnose）** — 找出与当天目标相比**最大的单一差距**（通常是蛋白质不足或碳水时机错误），量化到克数和百分比。
3. **调整（Adjust）** — 仅当触发条件满足时，给出**至多一条**基于证据的调整建议。无触发则回复「Hold — 本周无需调整」。

此外还包括：每 4 周一次结构化回顾、安全警戒线（体重下降过快、持续头晕、强迫性节食、力量退步+疲劳 → 建议暂停并咨询专业人士）。**瘦体重和运动表现优先于体重秤数字。**

## 饮食方案架构：三种日型

| 日型 | 场景 | 热量 | 蛋白质 | 碳水 | 脂肪 |
|---|---|---|---|---|---|
| 🔴 高碳日 | 练腿 / 大重量推 | 2,900 kcal | 150 g | 370 g | 60 g |
| 🟡 中碳日 | 拉类 / 容量训练 | 2,550 kcal | 150 g | 250 g | 70 g |
| 🟢 断食日 | 完全休息 | ~600 kcal | ~100 g | <30 g | 18 g |

**硬性规则：** 🔴 高碳仅在两个最大肌群训练日使用；🟢 断食日绝不训练。

## 安装方式（Claude Code / Claude Desktop）

将 `recomp-coach/` 文件夹放入 Claude 客户端的 skills 发现路径（如 `~/.claude/skills/`），或指向此仓库。Claude 加载 `SKILL.md`，其中的 `description` 字段控制自动触发条件。

```bash
git clone https://github.com/wangzhengjun571-alt/recomp-coach.git ~/.claude/skills/recomp-coach
```

## 科学依据

见 [`references/REFERENCES.md`](references/REFERENCES.md)。三篇经过同行评审的文献（MATADOR RCT、Seimon et al. 系统综述、Morton et al. 荟萃分析），每篇都标注了**支持的规则**和**外推效度限制**。

## 免责声明

面向健康成年人的教育工具，非医疗建议。间歇性能量限制的证据来自肥胖人群，外推到瘦体型个体是定性参考而非定量。开始前请咨询专业人士。

## 许可证

MIT — 见 [LICENSE](LICENSE)。
