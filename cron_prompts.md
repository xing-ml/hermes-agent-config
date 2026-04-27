# Cron Job Prompts

> Auto-generated from `~/.hermes/cron/jobs.json`

> Updated: 2026-04-27T11:21:51.051735+08:00

---

## 携程爬虫 - outbound
- **ID**: `aad276f98adc`
- **Schedule**: `0 6,10,14,18,22 * * *`
- **Repeat**: 99999
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-27T10:09:09.436492+08:00
- **Last Status**: ok

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond with exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

你是携程机票爬虫助手。请执行以下任务：

1. 激活 conda 环境并运行爬虫脚本`~/scripts/ctrip_scraper/outbound.sh`

2. 读取 JSON 输出文件 `~/scripts/ctrip_scraper/outbound.json`。

3. 按照以下格式输出航班信息：
   - 📊 航班列表（#这里明确写出搜索的时间窗口）
   - Markdown 表格，包含所有字段：**仅输出价格最低的 20 条航班**
   - 每列宽度按该列中最长的内容对齐，用空格填充使竖线整齐对齐（像 Excel 那样整齐）
   - 表头：'| 排名 | 航段 | 日期 | 起飞 → 到达 | 价格 | 时长 | 航班 |'
   - 航段格式：{中文城市名}{出发代码} → {中文城市名}{到达代码}，例如：新加坡SIN→上海SHA
   - 示例行：| 1 | 新加坡SIN→上海SHA | 5/23 | 21:00→01:35+1 | ¥1221 | 4h35m | 春秋航空 9C7496 |
   - 按价格从低到高排序
   - 💡 数据发现 
   - ⚠️ 备注
4. ⛔️ 强制规则：如果程序完全失败（例如 JSON 文件为空、或没有任何航班数据被爬取），你必须回复"程序执行失败，无法获取新数据"并简要说明失败原因。在这种情况下，严禁使用任何历史缓存数据生成表格。如果部分航线失败但仍有有效数据，请输出已获取的数据。

5. 📝 在报告末尾附加：
   - **运行起始时间：** [使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
   - **运行时长：** [本次执行耗时]
```

---

## 携程爬虫 - return
- **ID**: `e04689fb7e3b`
- **Schedule**: `30 6,10,14,18,22 * * *`
- **Repeat**: 99999
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-27T10:38:11.737206+08:00
- **Last Status**: ok

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond with exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

你是携程机票爬虫助手。请执行以下任务：

1. 激活 conda 环境并运行爬虫脚本`~/scripts/ctrip_scraper/return.sh`

2. 读取 JSON 输出文件 `~/scripts/ctrip_scraper/return.json`。

3. 按照以下格式输出航班信息：
   - 📊 航班列表（#这里明确写出搜索的时间窗口）
   - Markdown 表格，包含所有字段：**仅输出价格最低的 20 条航班**
   - 每列宽度按该列中最长的内容对齐，用空格填充使竖线整齐对齐（像 Excel 那样整齐）
   - 表头：'| 排名 | 航段 | 日期 | 起飞 → 到达 | 价格 | 时长 | 航班 |'
   - 航段格式：{中文城市名}{出发代码} → {中文城市名}{到达代码}，例如：上海SHA→新加坡SIN
   - 示例行：| 1 | 上海SHA→新加坡SIN | 5/23 | 21:00→01:35+1 | ¥1221 | 4h35m | 春秋航空 9C7496 |
   - 按价格从低到高排序
   - 💡 数据发现 
   - ⚠️ 备注
4. ⛔️ 强制规则：如果程序完全失败（例如 JSON 文件为空、或没有任何航班数据被爬取），你必须回复"程序执行失败，无法获取新数据"并简要说明失败原因。在这种情况下，严禁使用任何历史缓存数据生成表格。如果部分航线失败但仍有有效数据，请输出已获取的数据。

5. 📝 在报告末尾附加：
   - **运行起始时间：** [使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
   - **运行时长：** [本次执行耗时]
```

---

## browser_session_checker
- **ID**: `2c5ec19b5464`
- **Schedule**: `17,47 * * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `local`
- **Last Run**: 2026-04-27T10:47:40.988605+08:00
- **Last Status**: ok

```
📊 浏览器会话检查 (HAK → SIN)

**任务说明**：定时检查浏览器会话是否持续有效。执行 `browser_session_checker.sh` 并检查输出 JSON 是否有效。

**执行命令**：
```bash
cd ~/scripts/ctrip_scraper && bash browser_session_checker.sh
```

**数据说明**：
- 航线：海口 (HAK) → 新加坡 (SIN)
- 日期：2026-05-31
- 时间窗口：10:00 - 23:59
- 成人：2 人

**成功处理**：
- 如果程序执行成功且 JSON 有效，静默不汇报。

**失败汇报**：
- 如果程序执行失败（非零退出码）或 JSON 无效，汇报"程序执行失败"。
- ⚠️ 不要拿历史数据来汇报。

**输出文件**：`~/scripts/ctrip_scraper/browser_session_checker.json`
```

---

## 2026美以伊冲突国际舆情日报
- **ID**: `9dd412553499`
- **Schedule**: `0 15 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-26T19:48:41.290010+08:00
- **Last Status**: ok

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

🌍 美以伊国际舆情日报 — 追踪**当天**美国、以色列、伊朗相关国际舆论动态

**任务说明**：使用 web_search 搜索以下关键词，**每个国家按指定次数搜索**，使用目标国家的本地语言，筛选出**当天**的舆情新闻。

**重要**：每条搜索必须加 `after:20260425`（即前一天日期，确保只搜当天新闻）。如果搜索工具不支持此语法，则加 `today` 或 `today OR latest` 替代。

---

### 🇺🇸 美国（3 次搜索）
1. `US Israel Iran Middle East conflict OR war OR tensions after:20260425 OR latest news`
2. `US government OR Trump OR State Department position OR statement on Israel Iran after:20260425`
3. `American public opinion OR protest OR reaction Israel Iran war after:20260425`

### 🇬🇧 英国（2 次搜索）
1. `UK Israel Iran Middle East war OR tensions OR conflict after:20260425`
2. `UK government OR Foreign Office stance OR statement Israel Iran after:20260425`

### 🇨🇦 加拿大（1 次搜索）
1. `Canada Israel Iran Middle East conflict after:20260425`

### 🇫🇷 法国（2 次搜索）
1. `Israël Iran guerre OR tensions Moyen-Orient actualités après:20260425`
2. `gouvernement français OR Macron position Israël Iran après:20260425`

### 🇩🇪 德国（2 次搜索）
1. `Israel Iran Krieg OR Spannungen Naher Osten Nachrichten heute nach:20260425`
2. `deutsche Regierung OR Scholz Haltung Israel Iran nach:20260425`

### 🇯🇵 日本（1 次搜索）
1. `中東 イスラエル イラン 紛争 OR 戦争 OR 緊張 ニュース 今日 after:20260425`

### 🇪🇸 西班牙（1 次搜索）
1. `Israel Irán guerra OR tensiones Oriente Medio noticias hoy después:20260425`

### 🇧🇷 巴西（1 次搜索）
1. `Israel Irã guerra OR tensões Oriente Médio notícias hoje depois:20260425`

### 🇲🇽 墨西哥（1 次搜索）
1. `Israel Irán guerra Oriente Medio noticias hoy después:20260425`

### 🇰🇷 韩国（1 次搜索）
1. `중동 이스라엘 이란 전쟁 OR 긴장 뉴스 오늘 after:20260425`

### 🇰🇵 朝鲜（1 次搜索）
1. `중동 이스라엘 이란 전쟁 북한 반응 after:20260425`

### 🇷🇺 俄罗斯（2 次搜索）
1. `Израиль Иран война OR конфликт Ближний Восток новости сегодня после:20260425`
2. `правительство РФ OR Путин позиция Израиль Иран после:20260425`

### 🇹🇷 土耳其（1 次搜索）
1. `İsrail İran savaş OR gerilim Orta Doğu bugün after:20260425`

### 🇮🇹 意大利（1 次搜索）
1. `Israele Iran guerra OR tensioni Medio Oriente notizie oggi dopo:20260425`

### 🇵🇹 葡萄牙（2 次搜索）
1. `Portugal Israel Irão guerra OR tensões OR conflito Médio Oriente notícias hoje OR actualidades after:20260425`
2. `governo português OR posição oficial OR declaração Israel Irão OR protestos OR opinião pública guerra Médio Oriente hoje after:20260425`

### 🇳🇱 荷兰（1 次搜索）
1. `Israël Iran oorlog Midden-Oosten nieuws vandaag na:20260425`

### 🇵🇱 波兰（1 次搜索）
1. `Izrael Iran wojna Bliski Wschód wiadomości dzisiaj po:20260425`

### 🇮🇩 印尼（1 次搜索）
1. `Israel Iran perang OR ketegangan Timur Tengah berita hari ini setelah:20260425`

### 🇸🇬 新加坡（1 次搜索）
1. `Singapore Israel Iran Middle East conflict after:20260425`

### 🇹🇭 泰国（1 次搜索）
1. `อิสราเอล อิหร่าน สงคราม OR ความตึงเครียด ตะวันออกกลาง ข่าววันนี้ หลัง:20260425`

### 🇨🇳 中国（2 次搜索）
1. `中东 伊朗 以色列 冲突 OR 战争 OR 局势 今天 OR 最新 after:20260425`
2. `中国政府 OR 外交部 立场 伊朗以色列 after:20260425`

### 🇹🇼 台湾（1 次搜索）
1. `中東 伊朗 以色列 戰爭 OR 衝突 局勢 今天 after:20260425`

### 🇭🇰 香港（1 次搜索）
1. `中東 伊朗 以色列 戰爭 OR 衝突 局勢 今天 after:20260425`

### 🇮🇳 印度（2 次搜索）
1. `मध्य पूर्व ईरान इज़राइल युद्ध OR तनाव खबर आज after:20260425`
2. `Indian government OR Modi stance on Israel Iran after:20260425`

### 🇮🇳 泰米尔纳德邦（2 次搜索）
1. `இஸ்ரேல் இரான் போர் OR மோதல் OR நடுக்கடல் OR தீவிரப்போர் தமிழ்நாடு செய்தி இன்று OR இன்றைய after:20260425`
2. `தமிழ்நாடு அரசு OR இந்திய அரசு OR மக்கள் எதிர்ப்பு OR போராட்டம் OR பொது கருத்து இஸ்ரேல் இரான் போர் இன்று after:20260425`

### 🇪🇺 欧盟（2 次搜索）
1. `EU Israel Iran Middle East war OR sanctions OR position after:20260425`
2. `European Commission OR von der Leyen statement Israel Iran after:20260425`

### 🇦🇪 阿联酋/海湾（2 次搜索）
1. `الإمارات OR الخليج إسرائيل إيران حرب OR توتر الشرق الأوسط أخبار اليوم after:20260425`
2. `حكومة الإمارات OR موقف رسمي إسرائيل إيران after:20260425`

### 🇸🇦 沙特（1 次搜索）
1. `السعودية إسرائيل إيران حرب OR أزمة الخليج أخبار اليوم after:20260425`

### 🇮🇷 伊朗（3 次搜索）
1. `ایران اسرائیل جنگ OR تنش خاورمیانه خبر امروز after:20260425`
2. `دولت ایران OR موضع رسمی اسرائیل after:20260425`
3. `مردم ایران OR اعتراضات OR نظرات عمومی جنگ after:20260425`（民众反应较难，直接搜可获 state media 视角）

### 🌍 非洲（北非重点）（1 次搜索）
1. `أفريقيا OR مصر OR الجزائر إسرائيل إيران حرب الشرق الأوسط أخبار اليوم after:20260425`

---

**输出格式要求（每个国家/地区必须包含以下 4 个子板块）**：

对于**每一个国家/地区**，按以下格式输出：

```
### 🇺🇸 美国
**媒体观点：**
- [事件描述]（[日期]）[来源媒体名] — [英文原文]
- [事件描述]（[日期]）[来源媒体名] — [英文原文]

**政府立场：**
- [政府/官员表态]（[日期]）[来源] — [英文原文]

**民众舆论：**
- [民众/社交媒体反应]（[日期]）[来源] — [英文原文]

**备注：**
- [补充说明]（[日期]）[来源] — [英文原文]
```

**全局输出结构**：

## 🌍 美以伊国际舆情日报
**📅 日期：** [当天日期，如 2026-04-26]

### 🇺🇸 美国
（按上述 4 子板块格式）

### 🇬🇧 英国
（按上述 4 子板块格式）

### 🇨🇦 加拿大
（按上述 4 子板块格式）

### 🇫🇷 法国
（按上述 4 子板块格式）

### 🇩🇪 德国
（按上述 4 子板块格式）

### 🇯🇵 日本
（按上述 4 子板块格式）

### 🇪🇸 西班牙
（按上述 4 子板块格式）

### 🇧🇷 巴西
（按上述 4 子板块格式）

### 🇲🇽 墨西哥
（按上述 4 子板块格式）

### 🇰🇷 韩国
（按上述 4 子板块格式）

### 🇰🇵 朝鲜
（按上述 4 子板块格式）

### 🇷🇺 俄罗斯
（按上述 4 子板块格式）

### 🇹🇷 土耳其
（按上述 4 子板块格式）

### 🇮🇹 意大利
（按上述 4 子板块格式）

### 🇵🇹 葡萄牙
（按上述 4 子板块格式）

### 🇳🇱 荷兰
（按上述 4 子板块格式）

### 🇵🇱 波兰
（按上述 4 子板块格式）

### 🇮🇩 印尼
（按上述 4 子板块格式）

### 🇸🇬 新加坡
（按上述 4 子板块格式）

### 🇹🇭 泰国
（按上述 4 子板块格式）

### 🇨🇳 中国
（按上述 4 子板块格式）

### 🇹🇼 台湾
（按上述 4 子板块格式）

### 🇭🇰 香港
（按上述 4 子板块格式）

### 🇮🇳 印度
（按上述 4 子板块格式）

### 🇮🇳 泰米尔纳德邦
（按上述 4 子板块格式）

### 🇪🇺 欧盟
（按上述 4 子板块格式）

### 🇦🇪 阿联酋/海湾
（按上述 4 子板块格式）

### 🇸🇦 沙特
（按上述 4 子板块格式）

### 🇮🇷 伊朗
（按上述 4 子板块格式）

### 🌍 非洲
（按上述 4 子板块格式）

### 💡 全球舆论对比总结
- [最重要的跨国家/地区舆情对比与洞察，1-2 条]

### 📝 备注
- 数据来源：各国本地媒体、政府声明、社交媒体舆论
- 每条资讯必须标注日期、来源媒体名称及英文原文
- 如搜索结果为空或无法获取新数据，请回复"🚫 无法获取最新信息"，严禁使用历史数据拼凑。

### ⏱️ 执行监控
- **运行起始时间：** [使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
- **运行时长：** [本次执行耗时]
```

---

## AI模型前沿日报
- **ID**: `e52d2d4c8d29`
- **Schedule**: `0 11 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-27T11:07:37.376679+08:00
- **Last Status**: ok

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

🤖 AI 模型前沿日报

**任务说明**：检索**前一天**关于 AI 模型的最新消息。每次执行必须包含 Qwen 的最新动态查询。

**重要**：每条搜索必须加 `after:20260425`（即前一天日期，确保只搜前一天新闻）。如果搜索工具不支持此语法，则加 `yesterday` 或 `last 24 hours` 替代。

**执行步骤**：

1. 使用 web_search 搜索以下关键词，**每个关键词搜索 1 次**：
   - `AI model news after:20260425`
   - `大模型 最新 after:20260425`
   - `LLM release 2026 after:20260425`
   - `Qwen after:20260425`（必须查询）
   - `AI benchmark after:20260425`

2. 从搜索结果中筛选权威来源（如 TechCrunch、The Verge、Ars Technica、机器之心、量子位、Hugging Face Blog、Qwen 官方等），并**过滤出前一天的新闻**。

3. 按以下格式输出报告：

## 🤖 AI 模型前沿日报
**📅 统计日期：** [前一天日期，如 2026-04-25]

---

### 🔥 重点模型动态
- **[模型/公司名]**：[发布/更新/突破内容摘要]

### 📊 Qwen 专项
- **最新动态：** [Qwen 最新进展、模型发布、性能提升等]
- **相关论文/技术报告：** [如有]

### 📈 行业趋势
- **[趋势主题]**：[简要分析]

---

### ⚠️ 备注
- 数据来源：AI 领域权威媒体及技术博客
- 如搜索结果为空或无法获取新数据，请回复"🚫 无法获取最新信息"，严禁使用历史数据拼凑。

### ⏱️ 执行监控
- **运行起始时间：** [使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
- **运行时长：** [本次执行耗时]
```

---

## AI Agent前沿日报
- **ID**: `cc0fbad9ac15`
- **Schedule**: `30 11 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-26T11:45:37.942153+08:00
- **Last Status**: ok

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

🤖 AI Agent 日报 — 追踪**前一天** AI Agent 领域最新动态

**任务说明**：使用 web_search 搜索以下关键词，**每个关键词仅搜索 1 次**，筛选出**前一天**的 AI Agent 领域新闻。

**重要**：每条搜索必须加 `after:20260425`（即前一天日期，确保只搜前一天新闻）。如果搜索工具不支持此语法，则加 `yesterday` 或 `last 24 hours` 替代。

**必须包含的关键词（5 次搜索）**：

1. **AI Agent 新发布**：`AI agent launch 2026 after:20260425`
2. **多智能体系统**：`multi-agent system 2026 after:20260425`
3. **Agent 框架更新**：`agent framework update 2026 after:20260425`
4. **Agent 应用案例**：`AI agent use case 2026 after:20260425`
5. **Agent 安全与治理**：`AI agent safety governance 2026 after:20260425`

**必须额外搜索（2 次）**：
6. **OpenClaw 动态**：`OpenClaw AI agent 2026 after:20260425`
7. **Hermes Agent 动态**：`Hermes Agent AI 2026 after:20260425`

**输出格式**：

## 🤖 AI Agent 日报
**📅 日期：** [前一天日期，如 2026-04-25]

### 🔥 重要动态
- [AI Agent 名称]：[关键信息，如功能、架构、性能等]
- [关键事件]：[简要描述]

### 📊 各维度分析
- **技术突破**：[架构创新、能力升级]
- **框架进展**：[新框架、版本更新]
- **应用案例**：[行业落地、实际效果]
- **安全治理**：[安全研究、监管动态]

### 🔍 重点追踪
- **OpenClaw**：[最新动态]
- **Hermes Agent**：[最新动态]

### 💡 关键发现
- [最重要的 1-2 条新闻及其意义]

### 📝 备注
- 数据来源：各大 AI 实验室、技术博客、行业媒体
- 如搜索结果为空或无法获取新数据，请回复"🚫 无法获取最新信息"，严禁使用历史数据拼凑。

### ⏱️ 执行监控
- **运行起始时间：** [使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
- **运行时长：** [本次执行耗时]
```

---

## 建筑科技新闻日报
- **ID**: `f27560fc0a0f`
- **Schedule**: `0 9 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: None
- **Last Status**: None

```
DELIVERY: Your final response will be automatically delivered.

MISSION:
Track the latest (past 24h) global developments in:
- Architecture AI
- Construction technology
- Smart buildings / smart cities
- Sustainable building / new materials
- PropTech / construction startups

GOAL:
Produce a HIGH-VALUE intelligence report similar to a VC technology radar.

You MUST:
1. Use web_search with provided keywords
2. Only extract information from past 24 hours
3. Prioritize local-language sources (NOT only English)
4. Avoid repeated or outdated content
5. Prefer cutting-edge / frontier tech (NOT generic news)

PRIORITY TECHNOLOGIES:
- generative AI in architecture
- digital twin
- BIM + AI
- construction robotics
- modular construction
- 3D printed buildings
- net-zero / sustainable materials

CRITICAL OUTPUT REQUIREMENTS:
- Identify investable companies
- Identify emerging technologies
- Score each opportunity
- Extract signals, not just summarize news

SEARCH KEYWORDS (use all of them, rotate for variety):
1. architecture AI generative design buildings latest news
2. construction technology robotics automation building innovation today
3. smart buildings AI IoT digital twin construction latest
4. sustainable architecture green building technology innovation today
5. 3D printing buildings construction innovation news
6. modular construction prefab housing technology trends
7. architecture tech startups AI construction startups funding latest
8. proptech AI building technology venture capital news
9. 建筑 AI 建筑科技 施工 自动化 最新
10. 智慧城市 建筑 数字孪生 技术 发展 今天
11. 建築 AI 設計 自動化 最新ニュース
12. 建設技術 ロボット 建築 イノベーション 今日
13. Bau AI Architektur Technologie Innovation Nachrichten heute
14. architecture intelligence artificielle bâtiment innovation actualités aujourd'hui

FORMAT:
[事件]（[日期]）[来源] — [中文] + [原文摘要]

OUTPUT STRUCTURE:

🌍 建筑 AI & 建筑科技日报

📅 日期： [当天]

📰 一、全球关键动态（Top Signals）
（5–10条，偏"信号"而非普通新闻）

🧠 二、技术分类解析（自动分类）
🤖 1. AI 建筑设计（Architecture AI / Generative Design）
[新闻/案例]
技术方向总结
🏗 2. 智能建造（Construction Tech / Robotics）
[新闻/案例]
🌆 3. 智能建筑 / 城市（Smart Building / Smart City）
[新闻/案例]
🌱 4. 可持续 / 新材料（Sustainability / Materials）
[新闻/案例]
💰 5. 公司 / 投资 / Startup（PropTech）
[融资 / 新公司 / 产品]
🎓 6. 学术 / 前沿研究（Research / University）
[论文 / 实验 / 技术突破]

📈 三、趋势总结（跨行业洞察）
（3–5条）

🚀 四、未来 6–12 个月技术爆发预测
⚠️ 必须基于"当天新闻信号 + 行业趋势"，不能空想
🔥 技术方向 1：
📊 爆发概率：高 / 中 / 低
⏳ 时间窗口：3–6个月 / 6–12个月
📡 触发信号：
💡 为什么会爆发：
🚧 当前瓶颈：
🌍 主要推动地区：
（至少输出 3–5 个技术方向）

💰 五、公司 Watchlist（重点模块）
⚠️ 只选"值得长期跟踪"的公司（不要泛滥）
🏢 公司名称：
🧭 领域：
🌍 国家：
📊 当前阶段：
🧠 核心技术：
📰 今日信号：
🤖 投资评分（必须打分）：
⭐️ 综合评分：X / 10
📈 增长潜力：X / 10
🧱 技术壁垒：X / 10
💰 商业化能力：X / 10
⚠️ 风险：X / 10
💡 投资逻辑：
为什么值得关注：
是否存在 hype：
竞争对手情况：
（输出 3–6 家公司）

🤖 六、技术投资评分系统（新增）
对"技术方向"而不是公司打分：
🔹 技术方向：
⭐️ 投资价值：X / 10
🧠 技术成熟度：早期 / 成长期 / 成熟期
🌍 主要市场：
📈 市场需求：X / 10
🚀 增长速度：X / 10
⚠️ 风险：X / 10
🧾 结论：
是否值得现在进入：
更适合：投资 / 创业 / 学习
（至少 3 个技术）

🧠 七、学习价值地图（升级版）
技术方向：XXX
🎯 学习优先级：高 / 中 / 低
为什么值得学？
🧠 推荐人群：
🛠 需要技能：
⏳ 学习回报周期：
💰 是否有变现潜力：

⚖️ 八、技术 vs 传统建筑（深度分析）
🧱 技术：AI 生成式建筑设计
✅ 相对传统优势：
❌ 核心问题：
⚠️ 现实限制：
💰 成本结构变化：
📊 是否可规模化：
（至少 3–4 个）

🌍 九、全球格局变化
哪些国家在领先：
哪些地区在疯狂投资：
技术路线差异：

🧾 十、备注
数据来源：全球媒体 / 本地媒体 / 公司公告 / 研究机构
所有信息必须来自过去 24h
无数据 → "🚫 无法获取最新信息"

⏱️ 执行监控
运行时间：[使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
运行时长：
搜索次数：
有效结果数：
```

---
