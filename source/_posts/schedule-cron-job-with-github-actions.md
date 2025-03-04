---
title: 使用 GitHub Actions 调度定时任务
date: 2025-03-04
---

1. 在项目根目录创建 `.github/workflows` 目录。
2. 在 `workflows` 目录下创建 `schedule-cron-job.yml` 文件。
3. 在 `schedule-cron-job.yml` 文件中添加以下内容：

```yaml
name: 'Schedule Cron Job'

on:
  schedule:
    - cron: '30 1 * * 1-5'  # UTC 时间周一到周五 1:30 AM
  workflow_dispatch:  # 支持手动触发

jobs:
  send-notification:
    runs-on: ubuntu-latest
    
    steps:
      - name: Send GET request to Bark API
        run: |
          curl -X GET "https://api.day.app/your-token/title/content" 
```









