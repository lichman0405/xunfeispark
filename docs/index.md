## 文档

### PySparkAI 类

PySparkAI

#### 初始化

```python
ai = PySparkAI(app_id=APP_ID, api_key=API_KEY, api_secret=API_SECRET, spark_url=SPARK_URL, domain=DOMAIN)
```

参数:

- `app_id`: 您的应用ID
- `api_key`: 您的API密钥
- `api_secret`: 您的API秘密
- `spark_url`: 星火大模型的URL
- `domain`: 域名

#### 聊天方法

```python
response = ai.chat(messages, temperature=0.3, max_tokens=200)
```

参数:

- `messages`: 消息列表，其中每个消息都是一个字典，包括角色 (`system`, `user` 或 `assistant`) 和内容 (`content` 字段)。
- `temperature`: 控制模型的随机性。较高的值会产生更随机的输出，而较低的值会使其更确定。默认为 `None`。
- `max_tokens`: 输出的最大令牌数。这可以防止输出过长。默认为 `None`。

返回值:

- `choices`: 包含助理的回复消息的列表
- `usage`: 描述用于完成的令牌数量的字典

### 错误代码

若遇到与API交互时的问题，可以查阅`error_codes.py`获得错误码和相应描述。

例如:

```python
from error_codes import get_error_message
print(get_error_message(10001))
```

上述代码会返回对应错误码的描述：`"通过ws读取用户的消息出错"`