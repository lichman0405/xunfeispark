# SparkAI - WebSocket Chatbot Client for 星火大模型

SparkAI 是一个基于WebSocket调用星火大模型API的客户端。其目的是为用户提供高度封装的方法，从而简化使用过程。

## 特性

- 基于WebSocket的实时聊天：确保及时、持续的交互
- 星火大模型API：调用先进的AI技术来提供精确的回答
- 高度封装：减少配置和引导时间，即插即用

## 快速开始

### 安装

```bash
pip install sparkai
```

### 使用

查看demo.py脚本以了解如何使用SparkAI。以下是demo.py的简短摘要:

```python
from sparkai import SparkAI

def get_credentials_from_user():
    """
    获取用户输入的敏感信息。
    """
    APP_ID = "此处填入你的APP_ID"
    API_KEY = "此处填入你的API_KEY"
    API_SECRET = "此处填入你的API_SECRET"
    SPARK_URL = "此处填入你的SPARK_URL"
    DOMAIN = "此处填入你的DOMAIN"
	
    return APP_ID, API_KEY, API_SECRET, SPARK_URL, DOMAIN

# 以上所有信息都可以在你的讯飞开放平台的控制台中找到

def main():
    APP_ID, API_KEY, API_SECRET, SPARK_URL, DOMAIN = get_credentials_from_user()
    ai = SparkAI(app_id=APP_ID, api_key=API_KEY, api_secret=API_SECRET, spark_url=SPARK_URL, domain=DOMAIN)
    prompt_message = {"role": "system",
                      "content": "在一个遥远的星球上，有一位智者名为Zarnak，他对于人类世界有着深厚的了解。"}
    question_message = {"role": "user",
                        "content": "Zarnak, 你能告诉我地球上的人的性格为什么多种多样吗？"}
    format_specification_message = {
        "role": "system", "content": "请使用第三人称，以故事的方式回答。"}
    messages = [prompt_message, format_specification_message, question_message]
    completion = ai.chat(messages, temperature=0.3, max_tokens=200)
    formatted_answer = f"""
            Prompt: {prompt_message["content"]}
            格式要求: {format_specification_message["content"]}
            问题: {question_message["content"]}
            回答: {completion["choices"][0]["message"]}
            """
    print(formatted_answer)
    print("Token 使用情况:")
    for key, value in completion["usage"].items():
        print(f"{key}: {value}")


if __name__ == "__main__":
    main()

```

完整的demo.py脚本在仓库中可用。

## 开发

### 依赖

- `websocket-client`: 为项目提供WebSocket通信功能。

### 贡献

如果您想为该项目做出贡献，请确保遵循以下步骤：

1. Fork这个仓库: [SparkAI on GitLab](https://jihulab.com/lichman0405/sparkai.git)。当然，这里的GitLab是大陆本土化的**JihuLab**。
2. 创建你的功能分支 (`git checkout -b feature/YourFeature`)
3. 提交你的更改 (`git commit -am 'Add some feature'`)
4. 推送到分支 (`git push origin feature/YourFeature`)
5. 在GitLab上创建一个新的Merge Request

## 许可

该项目使用MIT许可。

## 联系

如有任何问题或建议，请联系 [shadow.li981@gmail.com](mailto:shadow.li981@gmail.com).

## 文档

更多关于 `sparkai` 的详细文档，包括如何安装、使用和其他信息，请访问 [这里](./docs/index.md)。
