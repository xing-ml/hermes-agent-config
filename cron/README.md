# Cron Jobs 配置目录

> Hermes Agent 定时任务系统

## 目录结构

```
cron/
├── templates/          # 输出模板（cronjob 报告格式）
│   ├── architecture_daily_template.md   # 建筑科技日报
│   ├── headhunter_daily_template.md     # 猎头日报
│   └── selfmedia_daily_template.md      # 自媒体日报
└── log/               # 运行日志（自动创建，每次运行前清空）
    ├── 建筑科技新闻日报.log
    ├── 猎头日报.log
    └── ...
```

## 模板系统

### 用途
长输出格式的 cronjob 使用模板文件，避免 prompt 过长被截断。

### 模板路径
```
~/scripts/hermes-agent-config/cron/templates/<name>_daily_template.md
```

### 使用方式
在 cronjob prompt 中引用：
```
1. Read the output template from: ~/scripts/hermes-agent-config/cron/templates/<name>_daily_template.md
```

### 创建新模板
1. 在 `templates/` 下新建 `<name>_daily_template.md`
2. 在 cronjob prompt 中引用模板路径
3. 更新 jobs.json 和 cron_prompts.md

## 日志系统

### 自动日志（所有 cronjob 已启用）

每个 cronjob 运行时会：
1. **开始** → 清空日志文件，写入开始时间
2. **每次搜索后** → 追加进度：`[时间] 搜索: <关键词>`
3. **结束** → 追加完成标记

### 日志路径
```
~/scripts/hermes-agent-config/cron/log/<job_name>.log
```

### 查看日志
```bash
cat ~/scripts/hermes-agent-config/cron/log/建筑科技新闻日报.log
```

## 当前 Cron Jobs

| 名称 | 时间 | 说明 |
|------|------|------|
| 携程爬虫 - outbound | 06:00, 10:00, 14:00, 18:00, 22:00 | 航班爬虫 |
| 携程爬虫 - return | 06:30, 10:30, 14:30, 18:30, 22:30 | 航班爬虫 |
| browser_session_checker | 每小时的 17,47 分 | 浏览器会话检查 |
| 2026美以伊冲突国际舆情日报 | 15:00 | 多国舆情监控 |
| AI模型前沿日报 | 11:00 | AI 模型新闻 |
| AI Agent前沿日报 | 11:30 | AI Agent 新闻 |
| 建筑科技新闻日报 | 09:00 | 建筑科技日报 |
| 猎头日报 | 07:00 | 岗位机会匹配 |
| 自媒体日报 | 17:00 | 自媒体趋势 |
| AI Agent Use Case | 16:00 | Reddit/X 用例收集 |

## 操作注意事项

### 新增 Cron Job
1. 创建 prompt（可引用模板）
2. 使用 `cronjob(action='create')` 创建
3. 如需模板，放入 `templates/`
4. 更新 `cron_prompts.md`

### 修改 Cron Job
1. 使用 `cronjob(action='update')` 修改
2. 如需改模板，修改 `templates/` 下对应文件
3. 更新 `cron_prompts.md`

### 模板修改规则
- ⚠️ 修改模板后，必须同步更新 jobs.json 中的 prompt
- ⚠️ 模板路径统一使用 `~/scripts/hermes-agent-config/cron/templates/`
- ⚠️ 不要修改 `~/.hermes/cron/templates/`（系统目录，保持同步）

### 日志管理
- 日志文件自动创建，无需手动管理
- 每次运行前自动清空
- 日志仅记录进度，不记录敏感数据
- 如需清理：`rm ~/scripts/hermes-agent-config/cron/log/*.log`

### Prompt 编写规范
- 使用 `[SYSTEM]` 前缀确保 Telegram 推送
- 每条搜索加时间过滤（`after:YYYYMMDD` 或 `today`）
- 每个国家/主题只搜 1 次
- 用本地语言搜索
- 日报搜前一天新闻，关键词去掉年份日期

## 文件同步

### 配置同步
- 本地：`~/scripts/hermes-agent-config/`
- GitHub：https://github.com/xing-ml/hermes-agent-config.git
- 所有修改需 git commit + push

### 模板同步
- 模板文件在 `cron/templates/` 下
- 与 `~/.hermes/cron/templates/` 保持同步
- 修改后 cp 到系统目录
