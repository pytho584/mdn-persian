---
title: "LanguageModel: contextWindow property"
short-title: contextWindow
slug: Web/API/LanguageModel/contextWindow
page-type: web-api-instance-property
browser-compat: api.LanguageModel.contextWindow
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`contextWindow`** در رابط {{domxref("LanguageModel")}} تعداد کل توکن‌های پنجره زمینه موجود برای این نشست را برمی‌گرداند. این مقدار هنگام ایجاد نشست تنظیم می‌شود و در طول عمر نشست تغییر نمی‌کند.

برای تعیین تعداد توکن‌های باقی‌مانده، `contextWindow` را با {{domxref("LanguageModel.contextUsage", "contextUsage")}} مقایسه کنید. از {{domxref("LanguageModel.measureContextUsage()", "measureContextUsage()")}} استفاده کنید تا قبل از ارسال، تخمین بزنید که یک درخواست جدید چند توکن مصرف می‌کند.

این مقدار به پیاده‌سازی وابسته است و بسته به مدل، قابلیت‌های دستگاه و پیکربندی نشست متفاوت است. مقدار `Infinity` نشان می‌دهد که عامل کاربر محدودیت سخت‌افزاری اعمال نمی‌کند.

## مقدار

عددی که ظرفیت پنجره زمینه نشست را بر حسب توکن نشان می‌دهد. اگر عامل کاربر محدودیت خاصی فراتر از حافظه موجود یا محدودیت‌های رشته جاوااسکریپت اعمال نکند، این مقدار می‌تواند `Infinity` باشد.

## مثال‌ها

### هشدار هنگامی که زمینه تقریباً پر است

در مثال زیر از یک تابع برای بررسی وجود زمینه کافی قبل از فراخوانی {{domson("LanguageModel.prompt()")}} استفاده می‌شود. ابتدا زمینه باقی‌مانده محاسبه و این مقدار به `measureContextUsage()` ارسال می‌شود. اگر `needed` کمتر یا مساوی `remaining` باشد، تابع `true` برمی‌گرداند و نشست ادامه می‌یابد.

```js
const promptText = "Let me ask you an interesting question...";

async function contextAvailable(promptText) {
  if (session.contextWindow === Infinity) {
    return true;
  }
  const remaining = session.contextWindow - session.contextUsage;
  const needed = await session.measureContextUsage(promptText);

  return needed <= remaining;
}

const session = await LanguageModel.create();

if (await contextAvailable(promptText)) {
  const response = await session.prompt(promptText);
  console.log(response);
} else {
  console.warn("Prompt skipped: Not enough context window remaining.");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LanguageModel.contextUsage")}}
- {{domxref("LanguageModel.measureContextUsage()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)