# تولید تصویر

endpoint سازگار با OpenAI Images API:

```http
POST /api/v1/images/generations
```

مدل را از [کاتالوگ](https://iranrouter.net/models) انتخاب کنید؛ مثلاً `openai/gpt-image-2.5-sunburst`.

## پایتون

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["IRANROUTER_API_KEY"],
    base_url="https://iranrouter.net/api/v1",
)

r = client.images.generate(
    model="openai/gpt-image-2.5-sunburst",
    prompt="a teal fox in the desert at dusk",
    size="1024x1024",
)

item = r.data[0]
print(item.url or item.b64_json)
```

## Node.js

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.IRANROUTER_API_KEY,
  baseURL: "https://iranrouter.net/api/v1",
});

const r = await client.images.generate({
  model: "openai/gpt-image-2.5-sunburst",
  prompt: "a teal fox in the desert at dusk",
  size: "1024x1024",
});

console.log(r.data[0].url || r.data[0].b64_json);
```

## curl

```bash
curl -sS https://iranrouter.net/api/v1/images/generations \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/gpt-image-2.5-sunburst",
    "prompt": "a teal fox in the desert at dusk",
    "size": "1024x1024"
  }'
```

## ادیت تصویر

```http
POST /api/v1/images/edits
```

```bash
curl https://iranrouter.net/api/v1/images/edits \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -F "model=openai/gpt-image-2.5-sunburst" \
  -F "prompt=make the background teal dusk sky" \
  -F "image=@source.png;type=image/png" \
  -F "size=1024x1024"
```

## مدل‌های دیگر تصویر

بسته به کاتالوگ زنده:

- OpenAI Images — مثل `openai/dall-e-3` یا خانوادهٔ GPT Image
- OpenRouter Image API — پارامترهایی مثل `resolution` و `aspect_ratio`
- BFL / FLUX — مثل `bfl/flux-2-pro`

جزئیات کامل: https://iranrouter.net/docs
