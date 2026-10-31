# اتصال OpenDesign به IranRouter

[OpenDesign](https://iranrouter.net/guides/open-design) را با API سازگار با OpenAI به IranRouter وصل کنید و موشن بسازید.
نسخهٔ زنده روی سایت: https://iranrouter.net/guides/open-design

زمان تقریبی: حدود ۵ دقیقه.

## پیش‌نیاز

کلید `ir-…` از https://iranrouter.net/dashboard/keys

## اتصال در ۶ قدم

1. کلید API را از داشبورد بسازید
2. در OpenDesign بروید به:

```text
Settings → Models & providers → API providers
```

3. یک Custom provider با پروتکل OpenAI-compatible بسازید
4. این مقادیر را وارد کنید:

| فیلد | مقدار |
|------|--------|
| API Key | کلید `ir-…` شما |
| Base URL | `https://iranrouter.net/api/v1` |
| Model ID | مثلاً `openai/gpt-4o-mini` |

5. دکمهٔ `Test` را بزنید و اتصال را ذخیره کنید
6. در پروژه همین اتصال را انتخاب کنید و Motion design بسازید

## نکات

- شناسهٔ مدل را دقیقاً از https://iranrouter.net/models کپی کنید
- به انتهای Base URL مسیر اضافی نچسبانید
- برای کار agentic روی HTML / موشن، مدل‌های قوی‌تر متن معمولاً نتیجهٔ بهتری می‌دهند

## اگر تصویر هم لازم دارید

برای تولید تصویر از endpoint جداگانه استفاده کنید؛ راهنما: [recipes/images.md](../recipes/images.md)

بعضی ابزارها بخش Media providers جدا دارند؛ Base URL و کلید همان IranRouter را آنجا هم می‌توانید بگذارید.

## رفع خطا

| کد | کار |
|----|-----|
| `401` | کلید را دوباره از داشبورد کپی کنید |
| `402` | اعتبار را شارژ کنید |
| `404` | Model ID را دقیق کنید |
| Test fail | اول با curl یا `GET /key` اتصال را جدا تست کنید |

## لینک‌ها

- راهنمای سایت: https://iranrouter.net/guides/open-design
- مستندات API: https://iranrouter.net/docs
- مدل‌ها: https://iranrouter.net/models
