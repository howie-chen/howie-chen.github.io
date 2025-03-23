---
title: 理解 OpenAI - Responses API
date: 2025-03-23 18:24:25
tags:
  - AI
  - OpenAI
categories:
  - AI 应用开发
--- 

OpenAI 最近推出了 Responses API，用于取代原有的 Chat Completions API，在其基础上封装了更多功能、简化了开发过程。这份笔记主要涵盖了 Responses API 的主要优势。

## 1. 省钱

聊天对话中，无需每个请求携带历史消息，很大程度减少了 token 的消耗，越多轮对话效果越明显，因为 Responses API 是有状态的。

![](/images/responses-api-comparison-with-chat-completions-api.png)

## 2. 内置工具

记得原先需要自己写代码通过 function calling 调用第三方 API 获取搜索结果，再回传给 LLM 生成最终结果，现在 web_search 直接内置了，请求当中包含 `tools: [ { type: "web_search_preview" } ]` 就完事了。

举个例子，通过以下几行代码，你就可以问最新股价了。

```typescript
import OpenAI from "openai";
const client = new OpenAI();

const response = await client.responses.create({
    model: "gpt-4o",
    tools: [ { type: "web_search_preview" } ],
    input: "What is the stock price of RingCentral, Inc. in March 23, 2025?",
});

console.log(response.output_text);
```

通过 Logs 你可以看到 web_search tool 被使用：
![](/images/openai-responses-api-built-in-web-search-logs.png)

在 API 返回体中，你可以拿到哪个网页被用于生成结果 <sup>[1](https://platform.openai.com/docs/guides/tools-web-search#output-and-citations)</sup>:
![](/images/web_search_tool_citation.png)

除了 web_search，内置的工具还有 file_search 和 computer_use，预计 code_interpreter 也将很快得到支持。

相信未来会有越来越多应用层的功能被内置到大模型的 API 当中，AI 应用的开发将会变得更简单。

## 参考文献

1. [This Perplexity thread](https://www.perplexity.ai/search/in-this-thread-i-m-going-to-le-h2eumQOAR5WAovEotFHCZw)
2. [Responses vs. Chat Completions](https://platform.openai.com/docs/guides/responses-vs-chat-completions)
3. [Built-in tools](https://platform.openai.com/docs/guides/tools?api-mode=responses)