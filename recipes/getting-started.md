# شروع سریع

هدف: در چند دقیقه به IranRouter وصل شوید.

## پیش‌نیاز

- حساب در [iranrouter.net](https://iranrouter.net/register)
- یک کلید API با پیشوند `ir-…`

## قدم‌ها

1. ثبت‌نام کنید: https://iranrouter.net/register
2. بروید به [داشبورد ← کلیدها](https://iranrouter.net/dashboard/keys)
3. یک کلید بسازید و کپی کنید
4. کلید را در محیط ذخیره کنید:

```bash
export IRANROUTER_API_KEY="ir-..."
```

5. Base URL را روی این مقدار بگذارید:

```text
https://iranrouter.net/api/v1
```

## احراز هویت

همهٔ endpointهای محافظت‌شده با این هدر کار می‌کنند:

```http
Authorization: Bearer ir-...
```

فقط خود کلید را بگذارید؛ بدون کلمهٔ `Bearer` داخل مقدار env، بدون فاصلهٔ اضافه، بدون کوتیشن اضافه در UI ابزارها.

## تست سریع با curl

```bash
curl https://iranrouter.net/api/v1/chat/completions \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek/deepseek-flash",
    "messages": [{"role": "user", "content": "سلام"}]
  }'
```

اگر پاسخ JSON با `choices` آمد، اتصال درست است.

## سطح رایگان

پس از ثبت‌نام، روی بعضی مدل‌ها سهمیهٔ رایگان دارید (معمولاً `deepseek/deepseek-flash` و `openai/gpt-4o-mini`).
جزئیات: https://iranrouter.net/docs#free-tier

وقتی سهمیه تمام شود و اعتبار نباشد، API معمولاً HTTP `402` برمی‌گرداند.

## بعدی

- [curl](curl.md)
- [پایتون](python.md)
- [Node.js](node.md)
- [بررسی کلید](check-key.md)
