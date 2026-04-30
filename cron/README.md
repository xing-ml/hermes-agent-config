# Cron Jobs 配置说明

## 目录结构

```
cron/
├── prompts/        # 各 job 的 prompt 文件
├── templates/      # 各 job 的报告模板
├── reports/        # 生成的日报（按日期归档）
├── log/            # 运行日志
└── README.md       # 本文件
```

## 命名规范

| 类型 | 文件路径 | 示例 |
|------|----------|------|
| Prompt | `prompts/{prefix}_prompt.md` | `prompts/ctrip_outbound_prompt.md` |
| Template | `templates/{prefix}_template.md` | `templates/ctrip_outbound_template.md` |
| Log | `log/{prefix}.log` | `log/ctrip_outbound.log` |
| Report | `reports/{prefix}_report_{YYYY_MM_DD}.md` | `reports/ctrip_outbound_report_2026-04-30.md` |

所有 4 部分共享同一个 `{prefix}` 前缀。

---

## Cron Job 清单

| # | Job ID | 名称 | 用途 | 频率 | 状态 | Prompt | Template |
|---|--------|------|------|------|------|--------|----------|
| 1 | `ai-agent` | AI Agent 日报 | 收集 AI Agent 领域每日新闻 | 每 12 小时 | 🟢 运行中 | `ai_agent_prompt.md` | `ai_agent_template.md` |
| 2 | `ai-model` | AI Model 日报 | 收集 AI Model 领域每日新闻 | 每 12 小时 | 🟢 运行中 | `ai_model_prompt.md` | `ai_model_template.md` |
| 3 | `con-tech` | 建筑施工科技日报 | 收集建筑科技领域每日新闻 | 每 12 小时 | 🟢 运行中 | `con_tech_prompt.md` | `con_tech_template.md` |
| 4 | `international-affairs` | 国际事务日报 | 收集国际时事每日新闻 | 每 12 小时 | 🟢 运行中 | `international_affairs_prompt.md` | `international_affairs_template.md` |
| 5 | `selfmedia` | 自媒体趋势分析 | 跨平台自媒体趋势报告 | 每 12 小时 | 🟢 运行中 | `selfmedia_prompt.md` | `selfmedia_template.md` |
| 6 | `headhunter` | 猎头日报 | 收集求职/猎头机会每日信息 | 每 12 小时 | 🟢 运行中 | `headhunter_prompt.md` | `headhunter_template.md` |
| 7 | `ctrip-outbound` | 携程出境航班 | 搜索出境航班（去程） | 每 12 小时 | 🟢 运行中 | `ctrip_outbound_prompt.md` | — |
| 8 | `ctrip-return` | 携程返程航班 | 搜索返程航班 | 每 12 小时 | 🟢 运行中 | `ctrip_return_prompt.md` | — |
| 9 | `browser-session-checker` | 浏览器会话检查 | 检查浏览器 session 有效性 | 每 30 分钟 | 🟢 运行中 | `browser_session_checker_prompt.md` | — |

---

## 工作流

### 新闻类日报（ai-agent, ai-model, con-tech, international-affairs, selfmedia, headhunter）

1. 定时触发 → 搜索前一天相关关键词新闻
2. AI 自动过滤和整理 → 按模板生成报告
3. 报告保存至 `reports/` → 推送至 Telegram
4. 运行日志写入 `log/{prefix}.log`

### 携程航班搜索（ctrip-outbound, ctrip-return）

1. 定时触发 → 浏览器自动化搜索航班
2. 解析结果 → 生成结构化报告
3. 报告保存至 `reports/` → 推送至 Telegram
4. 运行日志写入 `log/ctrip_*.log`

### 浏览器会话检查（browser-session-checker）

1. 每 30 分钟检查浏览器 session 状态
2. 如 session 失效则自动刷新 cookie

---

## 注意事项

- **Prompt 必须加 `[SYSTEM]` 前缀**，否则 Telegram 推送不生效
- 执行时区：GMT+8
- 修改 prompt 或 template 后，需更新对应的 cron job
- 所有 prompt 文件必须存在，否则 cron job 会静默失败
- 旧版 `cron_prompts.md` 已移除，统一使用 per-job prompt 文件
