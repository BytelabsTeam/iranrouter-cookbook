# Embeddings

برای تبدیل متن به بردار از `POST /embeddings` استفاده کنید.
شناسهٔ مدل را از [کاتالوگ](https://iranrouter.net/models) کپی کنید.

## پایتون

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["IRANROUTER_API_KEY"],
    base_url="https://iranrouter.net/api/v1",
)

r = client.embeddings.create(
    model="openai/text-embedding-3-small",
    input="سلام دنیا",
)

print(len(r.data[0].embedding))
print(r.data[0].embedding[:8])
```

## Node.js

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.IRANROUTER_API_KEY,
  baseURL: "https://iranrouter.net/api/v1",
});

const r = await client.embeddings.create({
  model: "openai/text-embedding-3-small",
  input: "سلام دنیا",
});

console.log(r.data[0].embedding.length);
```

## curl

```bash
curl -sS https://iranrouter.net/api/v1/embeddings \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/text-embedding-3-small",
    "input": "سلام دنیا",
    "encoding_format": "float"
  }'
```

## پارامترهای رایج

| فیلد | توضیح |
|------|--------|
| `model` | شناسهٔ مدل embedding |
| `input` | رشته یا آرایهٔ رشته |
| `dimensions` | اختیاری؛ بسته به مدل |
| `encoding_format` | معمولاً `float` |

مدل نمونه بالا را با slug واقعی کاتالوگ خودتان عوض کنید اگر در محیط شما فرق دارد.
