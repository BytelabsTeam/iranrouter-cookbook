# اتصال با پایتون

IranRouter با OpenAI Python SDK سازگار است.
فقط `base_url` و کلید را عوض کنید.

## نصب

```bash
pip install openai python-dotenv
```

یا helper رسمی:

```bash
git clone https://github.com/BytelabsTeam/iranrouterPython.git
cd iranrouterPython
pip install -r requirements.txt
```

## کلاینت مستقیم (OpenAI SDK)

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["IRANROUTER_API_KEY"],
    base_url="https://iranrouter.net/api/v1",
)

response = client.chat.completions.create(
    model="deepseek/deepseek-flash",
    messages=[{"role": "user", "content": "سلام"}],
)

print(response.choices[0].message.content)
```

## با helper ریپو

```python
from iranrouter import IranRouter

client = IranRouter()  # از IRANROUTER_API_KEY می‌خواند

response = client.chat.completions.create(
    model="openai/gpt-4o-mini",
    messages=[{"role": "user", "content": "Hello!"}],
)
print(response.choices[0].message.content)
```

## HTTP بدون SDK

```python
import os
import httpx

api_key = os.environ["IRANROUTER_API_KEY"]

r = httpx.post(
    "https://iranrouter.net/api/v1/chat/completions",
    headers={
        "Authorization": f"Bearer {api_key}",
        "Content-Type": "application/json",
    },
    json={
        "model": "deepseek/deepseek-flash",
        "messages": [{"role": "user", "content": "سلام"}],
    },
    timeout=60.0,
)
r.raise_for_status()
print(r.json()["choices"][0]["message"]["content"])
```

## فایل `.env`

```bash
IRANROUTER_API_KEY=ir-...
# اختیاری:
# IRANROUTER_BASE_URL=https://iranrouter.net/api/v1
```

## بعدی

- [استریم](streaming.md)
- [Embeddings](embeddings.md)
- [تصویر](images.md)
- ریپو: https://github.com/BytelabsTeam/iranrouterPython
