# browser_session_checker

**Job ID:** `2c5ec19b5464`

**Schedule:** 17,47 * * * *

**Status:** enabled

**Prompt:**

```
📊 浏览器会话检查 (HAK → SIN)

**任务说明**：定时检查浏览器会话是否持续有效。执行 `browser_session_checker.sh` 并检查输出 JSON 是否有效。

**步骤**：
1. 检查浏览器是否存活（`browser_alive.json` 存在且 `alive: true`）
2. 如果浏览器死亡，执行 `browser_start.sh` 启动
3. 执行 `browser_session_checker.sh` 检查会话
4. 读取 `~/scripts/ctrip_scraper/browser_session_checker.json` 输出结果

**输出格式**：
- 如果浏览器存活且会话有效，汇报"✅ 浏览器会话正常"
- 如果浏览器死亡，汇报"🔄 浏览器已重启"
- 如果会话失效，汇报"❌ 会话失效，已清除缓存"

**日志**：
- 时间窗口：10:00 - 23:59
- 成人：2 人

**成功处理**：
- 如果程序执行成功且 JSON 有效，静默不汇报。

**失败汇报**：
- 如果程序执行失败（非零退出码）或 JSON 无效，汇报"程序执行失败"。
- ⚠️ 不要拿历史数据来汇报。

**输出文件**：`~/scripts/ctrip_scraper/browser_session_checker.json`

📝 日志记录：将运行日志写入 ~/scripts/hermes-agent-config/cron/log/browser_session_checker.log，格式：[HH:MM:SS] 开始运行 / [HH:MM:SS] 搜索: {{KW}} / [HH:MM:SS] 运行完成
```
