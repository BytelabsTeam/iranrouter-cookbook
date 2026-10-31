# استریم (SSE)

با `"stream": true` پاسخ به‌صورت `text/event-stream` می‌آید و با `data: [DONE]` تمام می‌شود.
رفتار مثل OpenAI است.

## پایتون

```python
from openai import OpenAI
import os

client = OpenAI(
    api_key=os.environ["IRANROUTER_API_KEY"],
    base_url="https://iranrouter.net/api/v1",
)

stream = client.chat.completions.create(
    model="deepseek/deepseek-flash",
    messages=[{"role": "user", "content": "یک داستان کوتاه بگو"}],
    stream=True,
)

for chunk in stream:
    if not chunk.choices:
        continue
    text = chunk.choices[0].delta.content
    if text:
        print(text, end="", flush=True)
```

## Node.js

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.IRANROUTER_API_KEY,
  baseURL: "https://iranrouter.net/api/v1",
});

const stream = await client.chat.completions.create({
  model: "deepseek/deepseek-flash",
  messages: [{ role: "user", content: "یک داستان کوتاه بگو" }],
  stream: true,
});

for await (const chunk of stream) {
  const text = chunk.choices[0]?.delta?.content;
  if (text) process.stdout.write(text);
}
```

## curl

```bash
curl -N https://iranrouter.net/api/v1/chat/completions \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-flash",
    "stream": true,
    "messages": [{"role": "user", "content": "سلام"}]
  }'
```

## نکتهٔ usage

وقتی `stream_options.include_usage` true باشد (پیش‌فرض در بسیاری از مسیرها)، chunk نهایی می‌تواند `usage` داشته باشد.
جزئیات: https://iranrouter.net/docs
