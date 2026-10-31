# اتصال Kilo Code به IranRouter

افزونهٔ [Kilo Code](https://kilo.ai/) را در VS Code یا JetBrains به IranRouter وصل کنید.
نسخهٔ زنده روی سایت: https://iranrouter.net/guides/kilo

زمان تقریبی: حدود ۵ دقیقه.

## پیش‌نیاز

1. ثبت‌نام و کلید از https://iranrouter.net/dashboard/keys
2. نصب افزونهٔ Kilo Code در ادیتور

ورود به حساب خود Kilo لازم نیست؛ از کلید شخصی استفاده کنید.

## اتصال در ۶ قدم

1. کلید `ir-…` را از داشبورد بگیرید
2. پنل Kilo را در ادیتور باز کنید
3. بروید به:

```text
Settings → Providers → API Provider
```

4. مقدار `API Provider` را روی `OpenAI Compatible` بگذارید و فیلدها را پر کنید:

| فیلد | مقدار |
|------|--------|
| Base URL | `https://iranrouter.net/api/v1` |
| API Key | کلید `ir-…` شما |
| Model | مثلاً `deepseek/deepseek-flash` |

5. `Save` را بزنید (اسم پروفایل را مثلاً `IranRouter` بگذارید)
6. حالت را روی `Ask` بگذارید و یک سؤال کوتاه بپرسید

## نکات مهم

- در فیلد کلید فقط خود کلید را بگذارید؛ بدون `Bearer` و بدون کوتیشن
- به انتهای Base URL مسیر `/chat/completions` اضافه نکنید
- اگر فهرست مدل‌ها خودکار پر نشد، شناسه را دستی بنویسید

## مدل‌های رایگان رایج

- `deepseek/deepseek-flash`
- `openai/gpt-4o-mini`

هر پیام در Kilo ممکن است چند درخواست بفرستد (خواندن فایل / ابزار).
وقتی سهمیه تمام شد از https://iranrouter.net/dashboard/credits شارژ کنید.

## رفع خطا

| کد | کار |
|----|-----|
| `401` | کلید را دوباره کپی کنید |
| `402` | مدل رایگان بگذارید یا حساب را شارژ کنید |
| `404` | شناسهٔ مدل و Base URL را دقیق کنید |
| `429` | چند ثانیه صبر کنید؛ تسک را کوچک‌تر کنید |
| Timeout | پروکسی ادیتور / فیلترشکن را چک کنید |

## لینک‌ها

- راهنمای سایت: https://iranrouter.net/guides/kilo
- API رایگان: https://iranrouter.net/free-api
- مدل‌ها: https://iranrouter.net/models
