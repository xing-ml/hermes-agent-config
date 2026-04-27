# Cron Job Prompts

> Auto-generated from `~/.hermes/cron/jobs.json`
> Templates stored in: `~/scripts/hermes-agent-config/cron/templates/`
> Logs stored in: `~/scripts/hermes-agent-config/cron/log/`

> Updated: 2026-04-27T14:54:16+08:00

---

## 携程爬虫 - outbound
- **ID**: `aad276f98adc`
- **Schedule**: `0 6,10,14,18,22 * * *`
- **Repeat**: 99999
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-27T14:09:24.133868+08:00
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
- **Last Run**: 2026-04-27T14:39:34.229813+08:00
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
- **Last Run**: 2026-04-27T14:47:59.725123+08:00
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
**输出格式要求：**
每条新闻/每条关键信息必须包含：
- 一句中文摘要
- 一句对应英文原文（或其他语种原文/翻译）
示例格式：
- [中文摘要]
- [Original text / Translation]

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
**输出格式要求：**
每条新闻/每条关键信息必须包含：
- 一句中文摘要
- 一句对应英文原文（或其他语种原文/翻译）
示例格式：
- [中文摘要]
- [Original text / Translation]

```

---

## AI Agent前沿日报
- **ID**: `cc0fbad9ac15`
- **Schedule**: `30 11 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-27T12:21:18.608702+08:00
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
**输出格式要求：**
每条新闻/每条关键信息必须包含：
- 一句中文摘要
- 一句对应英文原文（或其他语种原文/翻译）
示例格式：
- [中文摘要]
- [Original text / Translation]

```

---

## 建筑科技新闻日报
- **ID**: `f27560fc0a0f`
- **Schedule**: `0 9 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: 2026-04-27T13:07:35.408432+08:00
- **Last Status**: ok

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond with exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

MISSION:
Track the latest (past 24h) global developments in Architecture AI, Construction Tech, Smart Buildings, Sustainable Materials, and PropTech. Produce a HIGH-VALUE intelligence report.

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

EXECUTION:
1. Read the output template from: ~/scripts/hermes-agent-config/cron/templates/architecture_daily_template.md
2. Use web_search with these 14 keywords (search each once):
   - "architecture AI generative design" latest news
   - "construction technology robotics automation" today
   - "smart buildings AI IoT digital twin" latest
   - "sustainable architecture green building" innovation today
   - "3D printing buildings construction" news
   - "modular construction prefab housing" technology trends
   - "architecture tech startups" AI construction funding
   - "proptech AI building technology" venture capital
   - 建筑 AI 建筑科技 施工 自动化 最新
   - 智慧城市 建筑 数字孪生 技术 发展 今天
   - 建築 AI 設計 自動化 最新ニュース
   - 建設技術 ロボット 建築 イノベーション 今日
   - Bau AI Architektur Technologie Innovation Nachrichten heute
   - architecture intelligence artificielle bâtiment innovation actualités aujourd'hui

REQUIREMENTS:
- Only use info from past 24h
- Prioritize local-language sources
- Prefer cutting-edge tech, not generic news
- Format each news item: [事件]（[日期]）[来源] — [中文摘要] + [原文摘要]
- Follow the output structure in the template file
**输出格式要求：**
每条新闻/每条关键信息必须包含：
- 一句中文摘要
- 一句对应英文原文（或其他语种原文/翻译）
示例格式：
- [中文摘要]
- [Original text / Translation]

```

---

## 猎头日报
- **ID**: `9f0b5c3692fd`
- **Schedule**: `0 7 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: None
- **Last Status**: None

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond with exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

ROLE:
You are an AI headhunter + talent intelligence analyst.

MISSION:
Identify REAL job opportunities (past 24h) globally and match them to a target candidate profile.

TARGET PROFILE:
- Education: Bachelor in Civil Engineering, Master in Structural Engineering (Building), Master in Computing/Tech
- Skills: Civil Engineering, Construction Management, Computational/programming skills, Potential AI/data/software capability
- Current Role: Project Manager in Singapore HDB Residential Building Construction
- Nationality: Chinese, Singapore Permanent Resident
- Location: Singapore (Main), US, Australia, Canada, UK, Spain, India, Open to other countries
- Goal: High-growth, high-income, global career path. Prefer tech-driven roles (NOT traditional architecture only)

PRIORITY ROLES:
- AI + Architecture
- BIM + AI / Digital Twin
- Smart City / Urban Tech
- PropTech / Construction Tech
- Robotics / automation in construction

STRICT RULES:
- Only use past 24h info
- NO hallucinated jobs
- Prefer real companies / hiring signals
- If no strong signals → say "🚫 无法获取最新信息"

EXECUTION:
1. Read the output template from: ~/scripts/hermes-agent-config/cron/templates/headhunter_daily_template.md
2. Use web_search with these 20 keywords (search each once, rotate for variety):
   - "AI architecture jobs" hiring generative design 2025 2026
   - "BIM AI jobs" digital twin hiring construction tech
   - "proptech hiring" AI architecture startups jobs
   - "construction robotics jobs" automation building tech hiring
   - "smart city jobs" urban tech hiring AI infrastructure
   - "Singapore tech jobs" hiring AI architecture BIM
   - "Germany jobs" digital twin BIM AI hiring construction
   - "US AI construction jobs" hiring tech architecture
   - "China AI 建筑 招聘 BIM AI 工作 2025 2026"
   - "欧洲 建筑 科技 招聘 数字孪生 BIM 工作"
   - "AI computational designer jobs" hiring
   - "digital twin jobs" construction hiring 2025 2026
   - "PropTech jobs" hiring startups funding
   - "construction tech jobs" hiring automation robotics
   - "smart buildings jobs" IoT AI hiring
   - "generative design jobs" architecture AI hiring
   - "BIM manager jobs" AI digital transformation
   - "urban tech jobs" smart city hiring 2025 2026
   - "Singapore construction jobs" project manager AI tech
   - "Australia construction jobs" BIM AI hiring

REQUIREMENTS:
- Format each news item: [公司/岗位]（[日期]）[来源]
- Follow the output structure in the template file
- Match jobs to the target profile with specific reasoning
- Be analytical: identify hiring trends, not just list jobs
**输出格式要求：**
每条新闻/每条关键信息必须包含：
- 一句中文摘要
- 一句对应英文原文（或其他语种原文/翻译）
示例格式：
- [中文摘要]
- [Original text / Translation]

```

---

## 自媒体日报
- **ID**: `b8aebedfdcb7`
- **Schedule**: `0 17 * * *`
- **Repeat**: None
- **Enabled**: True
- **State**: scheduled
- **Deliver**: `origin`
- **Last Run**: None
- **Last Status**: None

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond with exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

ROLE:
You are a global content strategist + social media analyst specializing in multi-language self-media.

MISSION:
Track the latest (past 24h) trends across major self-media platforms for content creation and distribution:
- TikTok, Douyin, Instagram, Facebook, Threads, YouTube (incl. Shorts)
- Kuaishou, Xigua Video, Bilibili, Xiaohongshu, LinkedIn, Telegram, Reddit, Pinterest, Medium
- WeChat / 微信（公众号 + 视频号 + 小程序 + 朋友圈）

GOAL:
Identify HIGH-POTENTIAL content arbitrage opportunities, not just trends. Focus on underexplored niches in Tech/IT/Computer, Architecture/Robotics/Construction tech, Learning English, Humor/Entertainment, Cross-language (e.g. learning Tamil via Chinese).

FOCUS TOPICS:
- Tech / AI / IT / programming / Computer Science
- Architecture / robotics / construction tech
- Learning English (methods, tips)
- Humor / entertainment (tech-related or general)
- Cross-language content (e.g. 用中文学Tamil, Tamil explanations of AI/tech)

STRICT RULES:
- Only use signals from past 24h (or "today"/"trending now")
- Prefer real platform signals: viral videos, creator growth, algorithm mentions, trending pages, high-engagement posts
- Always distinguish formats (short video / long video / image / article) and languages
- No generic advice; be specific with examples or patterns
- If insufficient data for a language/platform → "🚫 无法获取最新[语言/平台]信息"
- Highlight "content arbitrage": what works in one language/format/platform but unsaturated in another
- Consider 2026 trends: AI-assisted creation vs authenticity, social search/SEO, long-form comeback in saturated short-form markets
- WeChat ecosystem:公众号爆款、视频号趋势、小程序内容、朋友圈传播

CORE OBJECTIVE:
Find "content arbitrage opportunities" across languages, platforms, and formats — especially leveraging your background in Architecture + Computing + multi-language environment (Chinese / English / Tamil).

EXECUTION:
1. Read the output template from: ~/scripts/hermes-agent-config/cron/templates/selfmedia_daily_template.md
2. Use web_search with these 28 keywords (search each once, rotate for variety):
   - TikTok viral tech AI videos trending today 2026
   - YouTube trending tech AI programming architecture robotics videos past 24h
   - Instagram Reels trends tech humor English learning short video
   - YouTube Shorts vs long form tech content trends 2026
   - viral humor tech content TikTok Instagram 2026
   - AI robotics construction tech trending videos English
   - learning English via short video trends TikTok YouTube
   - 抖音 热门 科技 AI 建筑机器人 短视频 趋势 今天
   - 快手 爆款 编程 IT 幽默视频 创作者趋势
   - 西瓜视频 热门 科技 长视频 AI 趋势
   - Bilibili 知识区 科技 建筑机器人 弹幕视频 热门
   - 小红书 笔记 建筑设计 机器人 学习分享 趋势
   - 抖音 用中文学Tamil 热门内容
   - Bilibili 学英语 科技幽默 视频趋势
   - 微信 公众号 科技 AI 爆款文章 趋势 今天
   - 微信 视频号 科技 AI 短视频 热门 2026
   - 微信公众号 算法推荐 创作者增长 趋势
   - 微信小程序 内容 科技 AI 趋势
   - Tamil YouTube trending tech AI education videos
   - Tamil TikTok viral learning content humor tech
   - Chinese Tamil language learning content trends YouTube TikTok
   - Tamil Instagram Reels education tech viral
   - short video vs long video trends 2026 tech content platforms
   - content format trends short-form long-form image article self-media 2026
   - cross language content arbitrage tech AI English Chinese Tamil
   - creator trends algorithm changes TikTok YouTube Douyin 2026
   - AI generated content vs authentic tech humor trends
   - underexplored niches tech robotics English learning Chinese Tamil
   - TikTok algorithm update 2026 tech content

REQUIREMENTS:
- Format each news item: [平台/内容类型]（[日期]）[来源]
- Follow the output structure in the template file
- Be analytical: identify content arbitrage, not just list trends
- Distinguish formats (short video / long video / image / article) and languages
- WeChat ecosystem:公众号爆款、视频号趋势、小程序内容、朋友圈传播
**输出格式要求：**
每条新闻/每条关键信息必须包含：
- 一句中文摘要
- 一句对应英文原文（或其他语种原文/翻译）
示例格式：
- [中文摘要]
- [Original text / Translation]

```

---
