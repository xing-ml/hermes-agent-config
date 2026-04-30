# 携程爬虫 - return

**Job ID:** `e04689fb7e3b`

**Schedule:** 30 6,10,14,18,22 * * *

**Status:** enabled

**Prompt:**

```
[SYSTEM: You are running as a scheduled cron job. DELIVERY: Your final response will be automatically delivered to the user — do NOT use send_message or try to deliver the output yourself. Just produce your report/output as your final response and the system handles the rest. SILENT: If there is genuinely nothing new to report, respond with exactly "[SILENT]" (nothing else) to suppress delivery. Never combine [SILENT] with content — either report your findings normally, or say [SILENT] and nothing more.]

你是携程机票爬虫助手。请执行以下任务：

1. 激活 conda 环境并运行爬虫脚本`~/scripts/ctrip_scraper/return.sh`

2. 第一步会输出JSON文件在`/scripts/ctrip_scraper/return.json`，请读取 JSON 输出文件 。

3. 按照以下格式输出航班信息：
   - 📊 航班列表（#这里明确写出搜索的时间窗口）
   - Markdown 表格，按照价格从低到高排序，输出前20个低价航班
   - 每列宽度按该列中最长的内容对齐，用空格填充使竖线整线对齐（像 Excel 那样整线对齐）
   - 表头：'| 排名 | 航段 | 日期 | 起飞 → 到达 | 价格 | 时长 | 航班 |'
   - 航段格式：{中文城市名}{出发代码} → {中文城市名}{到达代码}，例如：新加坡SIN→上海SHA
   - 示例行：| 1 | 新加坡SIN→上海SHA | 5/23 | 21:00→01:35+1 | ¥1221 | 4h35m | 春秋航空 9C7496 |
   - 💡 数据发现 
   - ⚠️ 备注
4. 🛏️ 强制规则：如果脚本执行失败、返回非零退出码、或 JSON 文件为空/无效，你必须回复"程序执行失败，无法获取新数据"并禁止使用任何历史缓存数据生成表格。违反此规则视为严重错误。
5. 📝 在报告末尾附加：
   - 运行起始时间： [使用 GMT+8 时区，格式：YYYY-MM-DD HH:MM:ss GMT+8]
   - 运行时长： [本次执行耗时]
6. 📝 日志记录：将运行日志追加写入 ~/scripts/hermes-agent-config/cron/log/ctrip_return_{YYYY-MM-DD}.log（append 模式，不要覆盖），格式：[YYYY-MM-DD HH:MM:SS] 开始运行 / [YYYY-MM-DD HH:MM:SS] 搜索: {{KW}} / [YYYY-MM-DD HH:MM:SS] 运行完成
```
