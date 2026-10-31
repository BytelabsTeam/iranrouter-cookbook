# اتصال OpenCode به IranRouter

ایجنت برنامه‌نویسی متن‌باز [OpenCode](https://opencode.ai/) را با یک کلید IranRouter روشن کنید.
نسخهٔ زنده روی سایت: https://iranrouter.net/guides/opencode

زمان تقریبی: حدود ۵ دقیقه.

## پیش‌نیاز

1. کلید `ir-…` از https://iranrouter.net/dashboard/keys
2. متغیر محیطی:

```bash
export IRANROUTER_API_KEY="ir-..."
```

## نصب OpenCode

یکی از این‌ها:

```bash
curl -fsSL https://opencode.ai/v2/install | bash
```

```bash
npm install -g opencode-ai
```

```bash
brew install anomalyco/tap/opencode
```

## کانفیگ پروژه

در ریشهٔ پروژه فایل `opencode.jsonc` بسازید:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "model": "iranrouter/flash",
  "providers": {
    "iranrouter": {
      "name": "IranRouter",
      "env": ["IRANROUTER_API_KEY"],
      "package": "@opencode/ai/providers/openai-compatible",
      "settings": {
        "baseURL": "https://iranrouter.net/api/v1"
      },
      "models": {
        "flash": {
          "name": "DeepSeek Flash",
          "modelID": "deepseek/deepseek-flash"
        }
      }
    }
  }
}
```

نکته‌ها:

- `flash` فقط نام کوتاه داخل OpenCode است
- `modelID` همان شناسهٔ واقعی کاتالوگ IranRouter است
- به انتهای `baseURL` مسیر `/chat/completions` اضافه نکنید

## انتخاب مدل

```bash
opencode
```

سپس:

```text
/models → iranrouter/flash
```

اگر از `/connect` استفاده می‌کنید، گزینهٔ Other را بزنید و شناسهٔ provider را `iranrouter` بگذارید.

## تست

با `/init` پروژه را راه‌اندازی کنید و یک تسک کوچک بفرستید؛ مثلاً فقط توضیح ساختار پروژه بدون ویرایش فایل.

## رفع خطا

| کد | کار |
|----|-----|
| `401` | `IRANROUTER_API_KEY` را چک کنید؛ فقط خود کلید |
| `402` | سهمیه تمام شده — حساب را شارژ کنید |
| `404` | `modelID` و `baseURL` را دقیق کنید |
| Config | شناسهٔ provider باید `iranrouter` باشد و فایل در ریشهٔ پروژه باشد |

## لینک‌ها

- راهنمای سایت: https://iranrouter.net/guides/opencode
- مدل‌ها: https://iranrouter.net/models
- شارژ: https://iranrouter.net/dashboard/credits
