# اتصال با Node.js

IranRouter با OpenAI Node SDK سازگار است.
فقط `baseURL` و کلید را عوض کنید.
Node.js 18+ لازم است (`fetch` داخلی).

## نصب

```bash
npm install openai dotenv
```

یا helper رسمی:

```bash
git clone https://github.com/BytelabsTeam/iranrouter-node.git
cd iranrouter-node
npm install
```

## کلاینت مستقیم (OpenAI SDK)

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.IRANROUTER_API_KEY,
  baseURL: "https://iranrouter.net/api/v1",
});

const response = await client.chat.completions.create({
  model: "deepseek/deepseek-flash",
  messages: [{ role: "user", content: "سلام" }],
});

console.log(response.choices[0].message.content);
```

## با helper ریپو

```js
import { IranRouter } from "iranrouter"; // یا از src/index.js

const client = IranRouter(); // از IRANROUTER_API_KEY می‌خواند

const response = await client.chat.completions.create({
  model: "openai/gpt-4o-mini",
  messages: [{ role: "user", content: "Hello!" }],
});
console.log(response.choices[0].message.content);
```

## HTTP بدون SDK

```js
const apiKey = process.env.IRANROUTER_API_KEY;

const res = await fetch("https://iranrouter.net/api/v1/chat/completions", {
  method: "POST",
  headers: {
    Authorization: `Bearer ${apiKey}`,
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    model: "deepseek/deepseek-flash",
    messages: [{ role: "user", content: "سلام" }],
  }),
});

const data = await res.json();
console.log(data.choices[0].message.content);
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
- ریپو: https://github.com/BytelabsTeam/iranrouter-node
