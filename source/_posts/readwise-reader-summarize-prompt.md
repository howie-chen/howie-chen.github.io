---
title: 我的 Readwise Reader 文章摘要提示词
date: 2025-03-10 12:00:00
tags:
  - Readwise Reader
  - AI
  - Prompt
categories:
  - 信息输入系统
---

```
{#- 简体中文摘要 -#}

{#- 下面的 Prompt 会将文档缩减成一个 300 字内的摘要，并根据你的 highlight 进行重点摘要。-#}

请使用 300 字以内，以简体中文总结以下文本：

"""

标题：{{ document.title }}
作者：{{ document.author }} 
来源：{{ document.domain }}

另外，在阅读此文章时，我对以下部分进行了高亮，认为这些是文章的重点，给你学习参考：

{% for highlight in document.highlights %}
- {{ highlight.content }}
{% endfor %}

{#- 下面的 if-else 逻辑检查文档的长度。如果文档较长，它将使用关键句子以避免超出 GPT 提示窗口的限制。我们强烈建议除非您知道自己在做什么，否则不要更改此设置。-#}

{% if (document.content | count_tokens) > 2000 %}
{{ document.content | central_sentences | join('\n\n') }}
{% else %}
{{ document.content }}
{% endif %}

"""

重要提示：请不要超过 300 字。每句话应该简洁易读；关于中文的排版原则：在中文和英文或数字之间，要有一个半角空白，例如：Apple 手机；3 个 AI 工具。
```

![](/images/hunt-good-weekly.jpeg)