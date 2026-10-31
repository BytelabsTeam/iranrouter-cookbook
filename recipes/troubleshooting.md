# رفع خطاهای رایج

| کد | معنی تقریبی | کار |
|----|-------------|-----|
| `401` | کلید نامعتبر | کلید را از داشبورد دوباره کپی کنید. فقط `ir-…`؛ بدون `Bearer` داخل env یا فیلد UI |
| `402` | سهمیه / اعتبار کافی نیست | مدل رایگان بگذارید یا حساب را شارژ کنید: https://iranrouter.net/dashboard/credits |
| `404` | مدل یا مسیر پیدا نشد | شناسهٔ مدل را دقیقاً از کاتالوگ کپی کنید. به Base URL مسیر تکراری اضافه نکنید |
| `422` / validation | بدنهٔ درخواست غلط | فیلدهای `model` و `messages` را با docs چک کنید |
| `429` | نرخ زیاد | چند ثانیه صبر کنید؛ حدود ۶۰ درخواست / ۶۰ثانیه به ازای هر کلید |
| Timeout | پاسخی نمی‌آید | پروکسی / فیلترشکن و DNS را چک کنید؛ اول با curl تست کنید |

## اشتباه‌های پرتکرار Base URL

درست:

```text
https://iranrouter.net/api/v1
```

غلط:

```text
https://iranrouter.net/api/v1/chat/completions
https://iranrouter.net/api/v1/v1
https://iranrouter.net
```

SDK خودش مسیر endpoint را اضافه می‌کند.

## چک‌لیست سریع

1. `GET /key` موفق است؟ → [بررسی کلید](check-key.md)
2. همان کلید در `Authorization: Bearer …` است؟
3. مدل از [کاتالوگ](https://iranrouter.net/models) کپی شده؟
4. با [curl](curl.md) خام جواب می‌آید؟

اگر هنوز گیر کردید:

- مستندات: https://iranrouter.net/docs
- پشتیبانی داخل داشبورد: https://iranrouter.net/dashboard/support
- یا در [Issues همین ریپو](https://github.com/BytelabsTeam/iranrouter-cookbook/issues) بنویسید
