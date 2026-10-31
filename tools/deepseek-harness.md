# اتصال DeepSeek Harness به IranRouter

ایجنت متن‌باز [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) را با Custom model API به IranRouter وصل کنید.
نسخهٔ زنده روی سایت: https://iranrouter.net/guides/deepseek-harness

زمان تقریبی: حدود ۵ دقیقه.

## نصب / اجرا

سریع:

```bash
npx @deepseek-ai/dsh web
```

یا از سورس:

```bash
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

## اتصال در ۶ قدم

1. کلید `ir-…` را از https://iranrouter.net/dashboard/keys بگیرید
2. Harness را اجرا کنید
3. بروید به:

```text
Settings → Models → Add model provider
```

4. تب را از `Third-party model provider` به `Custom model API` عوض کنید
5. فیلدها را این‌طور پر کنید:

| فیلد | مقدار |
|------|--------|
| Provider ID | `iranrouter` |
| Display name | `IranRouter` |
| Base URL | `https://iranrouter.net/api/v1` |
| API protocol | `OpenAI Chat Completions` |
| API key | کلید `ir-…` شما |

6. Model ID را از کاتالوگ بگذارید (مثلاً `deepseek/deepseek-flash`)، `Create provider` را بزنید و یک پیام تست بفرستید

## نکات

- `Provider ID` بعداً قابل تغییر نیست؛ با حروف کوچک انگلیسی بنویسید
- به انتهای Base URL مسیر `/chat/completions` اضافه نکنید
- در فیلد کلید فقط خود کلید را بگذارید

## سازگاری اختیاری

اگر مدل شما بعضی فیلدهای پیشرفته را پشتیبانی نمی‌کند، می‌توانید در تنظیمات پیشرفته/compat مقادیری شبیه این بگذارید:

```yaml
- id: llm-pi-ai
  config:
    providers:
      iranrouter:
        compat:
          supportsDeveloperRole: false
          maxTokensField: max_tokens
```

جزئیات بیشتر در راهنمای سایت.

## رفع خطا

| کد | کار |
|----|-----|
| `401` | کلید را دوباره کپی کنید |
| `402` | حساب را شارژ کنید |
| `404` | Model ID و Base URL را دقیق کنید |
| پروتکل | حتماً `OpenAI Chat Completions` باشد |

## لینک‌ها

- راهنمای سایت: https://iranrouter.net/guides/deepseek-harness
- مدل‌ها: https://iranrouter.net/models
- شارژ: https://iranrouter.net/dashboard/credits
