# بررسی کلید و اعتبار

قبل از دیباگ کردن اپ، وضعیت کلید را چک کنید.

```http
GET /api/v1/key
Authorization: Bearer $IRANROUTER_API_KEY
```

## curl

```bash
curl -sS https://iranrouter.net/api/v1/key \
  -H "Authorization: Bearer $IRANROUTER_API_KEY" | python3 -m json.tool
```

## پایتون

```python
import os
import httpx

r = httpx.get(
    "https://iranrouter.net/api/v1/key",
    headers={"Authorization": f"Bearer {os.environ['IRANROUTER_API_KEY']}"},
    timeout=30.0,
)
r.raise_for_status()
print(r.json())
```

## Node.js

```js
const res = await fetch("https://iranrouter.net/api/v1/key", {
  headers: { Authorization: `Bearer ${process.env.IRANROUTER_API_KEY}` },
});
console.log(await res.json());
```

## چه چیزی برمی‌گردد؟

پاسخ معمولاً شامل مواردی مثل این‌هاست:

- `is_free_tier`
- `free_models`
- `topup_url`

اگر `401` گرفتید، کلید اشتباه یا منقضی است.
اگر سهمیه رایگان تمام شده باشد، درخواست chat ممکن است `402` بدهد — از [شارژ اعتبار](https://iranrouter.net/dashboard/credits) استفاده کنید.
