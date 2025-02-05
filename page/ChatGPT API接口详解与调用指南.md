# ChatGPT API接口详解与调用指南

## OpenAI API简介

OpenAI API 是一种开放的应用程序编程接口，开发者可以通过该接口访问 OpenAI 开发的 ChatGPT 模型。ChatGPT API 是 OpenAI API 的一个具体实现，基于 ChatGPT 模型提供人工智能服务接口。通过 ChatGPT API，开发者可以构建各种对话应用程序，如聊天机器人、虚拟助手等，提升应用程序的自然语言处理能力。

![OpenAI API](https://bbtdd.com/img/7093756115189535.webp)

OpenAI 提供了两种相似但又不同的 API：ChatCompletion 和 Completion。ChatCompletion 的底层模型是 GPT-3.5 和 GPT-4.0，而 Completion 的底层模型是 text-davinci-003。那么在实际开发中应该如何选择呢？

OpenAI 官方建议使用 GPT-4 或 GPT-3.5-turbo，根据任务的复杂程度进行选择。一般来说，GPT-4 在各种评估中表现更好，尤其是在遵循复杂指令方面。相比之下，GPT-3.5-turbo 更可能只遵循复杂指令中的一部分。GPT-4 更不容易编造信息，且上下文窗口更大（8192 个标记），而 GPT-3.5-turbo 只有 4096 个标记。但 GPT-3.5-turbo 的输出延迟较低，且每个标记的成本更低。因此，开发中应首选 ChatCompletion 接口。

## OpenAI 接口的基本收费标准

OpenAI 的接口收费标准主要分为两种情况：针对网页版会话的普通用户和通过 API 调用模型的开发者。对于开发者，OpenAI API 调用费用的核心计算方式是基于“token”的数量。这里的“token”指的是分解单元，中文大致等同于一个词。需要注意的是，OpenAI 会根据用户存储的信息和使用量进行收费。例如，ChatGPT 提供了一定数量的 API 调用额度，如果超出套餐额度，则需按照每 100 万个 API 调用收费 2 美元的标准进行计费。

下图是 OpenAI 官方给出的 GPT-3.5 Turbo 和 GPT-4 的 API 调用收费标准（数据获取时间为 2023 年 11 月 1 日）：

![OpenAI API 收费标准](https://bbtdd.com/img/13239776384400.webp)

## ChatGPT API 接口使用指南

要调用 ChatGPT API 接口，您需要完成以下几个步骤：

1. **注册 OpenAI 账号并获得 API 密钥**  
   API key 可以在 OpenAI 官网的 API Keys 处获取。请注意，API key 只能显示一次，务必妥善保存。同时，在 Billing 中设置好银行卡以确定付款方式。

2. **选择合适的编程语言**  
   根据您的需求和应用场景，选择合适的编程语言（如 Python、JavaScript、Java 等）进行 API 调用。

3. **安装必要的库或模块**  
   根据所选编程语言，安装必要的库或模块，以便在代码中发起 HTTP 请求。

4. **编写代码**  
   根据官方文档配置 API 请求参数，如输入文本、生成文本长度等。在代码中加入您的 API 密钥以进行身份验证。

5. **发起 API 请求**  
   运行编写好的代码，发起 API 请求。成功调用后，ChatGPT 将返回相应的结果，如生成的文本或情感分析结果等。

6. **处理 API 响应**  
   对 API 返回的结果进行处理，并将其集成到您的应用、网站或服务中。

### Python 调用示例

python
import openai

# Basic chatting
messages = [
    {"role": "system", "content": "You give very short answers"},
    {"role": "user", "content": "How are you today?"},
]

openai.api_key = OPENAI_API_KEY
response = openai.ChatCompletion.create(
    model=GPT_MODEL,
    messages=messages
)

print(response)


说明：`messages` 包含用户对 GPT 的指示和问题。`role: system` 是给 GPT 的系统提示，本例中要求 GPT 以尽可能短的方式回答以减少 token 使用量。`role: user` 代表我们向 GPT 提出的问题。

返回结果如下：

json
{
    "id": "chatcmpl-84cWIIkggMl6kl48XeZQJBNv4wLar",
    "object": "chat.completion",
    "created": 1696112074,
    "model": "gpt-3.5-turbo-0613",
    "choices": [
        {
            "index": 0,
            "message": {
                "role": "assistant",
                "content": "I am fine."
            },
            "finish_reason": "stop"
        }
    ],
    "usage": {
        "prompt_tokens": 22,
        "completion_tokens": 4,
        "total_tokens": 26
    }
}


GPT 返回一个 JSON 格式的对象，包含调用的基本信息、回复信息以及 token 使用情况。可以通过 `response["choices"][0]["message"]["content"]` 提取回复内容。

## 使用 ChatGPT API 的注意事项

1. **优化输入**  
   精心设计输入提示，明确指示希望获得的回答或建议，以提高生成文本的质量。

2. **处理输出**  
   检查输出文本的质量和可用性，通过预处理和后处理步骤优化输出，如过滤敏感内容、删除无关信息等。

3. **限制使用**  
   关注 API 使用情况，确保不超出配额。通过 API 控制台查看调用次数、使用量、错误率等统计数据。

4. **错误处理**  
   妥善处理 API 可能返回的错误，如请求超时、无效的 API 密钥等，设计异常处理机制提高程序稳定性。

5. **保持更新**  
   定期关注官方更新信息，了解新功能和性能改进，注意 API 版本变更可能带来的兼容性问题。

## ChatGPT API 的应用场景

ChatGPT API 可用于各种应用场景，包括但不限于：

- **聊天机器人**：构建智能聊天机器人，实现自然、流畅、智能的对话。
- **虚拟助手**：集成到虚拟助手中，帮助用户解答问题、提供建议等。
- **智能客服**：提供高效的客服支持，解答用户问题和解决问题。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)
