# اتصال با curl

ساده‌ترین راه برای تست API بدون SDK.

## چت

```bash
export IRANROUTER_API_KEY="ir-..."

curl https://iranrouter.net/api/v1/chat/completions \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-flash",
    "messages": [{"role": "user", "content": "سلام! خودت را در یک جمله معرفی کن."}]
  }'
```

خروجی را خواناتر کنید:

```bash
curl -sS https://iranrouter.net/api/v1/chat/completions \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-flash",
    "messages": [{"role": "user", "content": "سلام"}]
  }' | python3 -m json.tool
```

## فهرست مدل‌ها

```bash
curl -sS https://iranrouter.net/api/v1/models \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" | python3 -m json.tool
```

## وضعیت کلید

```bash
curl -sS https://iranrouter.net/api/v1/key \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" | python3 -m json.tool
```

## استریم

```bash
curl -N https://iranrouter.net/api/v1/chat/completions \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-flash",
    "stream": true,
    "messages": [{"role": "user", "content": "یک داستان کوتاه بگو"}]
  }'
```

پاسخ به‌صورت SSE می‌آید و با `data: [DONE]` تمام می‌شود.

## Embeddings

```bash
curl -sS https://iranrouter.net/api/v1/embeddings \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/text-embedding-3-small",
    "input": "سلام دنیا"
  }' | python3 -m json.tool
```

مدل embedding را از [کاتالوگ](https://iranrouter.net/models) انتخاب کنید.

## تصویر

```bash
curl -sS https://iranrouter.net/api/v1/images/generations \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/gpt-image-2.5-sunburst",
    "prompt": "a teal fox in the desert at dusk",
    "size": "1024x1024"
  }' | python3 -m json.tool
```

## نکات

- Base URL همان `https://iranrouter.net/api/v1` است؛ مسیر endpoint را جدا اضافه کنید.
- کلید را با `export` ست کنید تا در تاریخچهٔ شل کمتر دیده شود.
- نمونهٔ آماده: [iranrouter-examples/curl](https://github.com/BytelabsTeam/iranrouter-examples)
