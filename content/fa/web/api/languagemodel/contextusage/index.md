---
title: "LanguageModel: contextUsage property"
short-title: contextUsage
slug: Web/API/LanguageModel/contextUsage
page-type: web-api-instance-property
browser-compat: api.LanguageModel.contextUsage
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`contextUsage`** از رابط {{domxref("LanguageModel")}}، تعداد توکن‌های پنجرهٔ زمینه (context window) را که در حال حاضر توسط نشستِ فراخواننده مصرف شده است برمی‌گرداند؛ این تعداد شامل درخواست‌های اولیه و تمام نوبت‌های بعدی نیز می‌شود.

این مقدار هر بار که یکی از متدهای {{domxref("LanguageModel.prompt()", "prompt()")}}، {{domxref("LanguageModel.promptStreaming()", "promptStreaming()")}} یا {{domxref("LanguageModel.append()", "append()")}} را فراخوانی کنید، افزایش می‌یابد.

برای تعیین اینکه چند توکن باقی مانده است، `contextUsage` را با {{domxref("LanguageModel.contextWindow")}} مقایسه کنید. اگر `contextUsage` از `contextWindow` تجاوز کند، در فراخوانی‌های بعدی متدها یک خطای `QuotaExceededError` پرتاب می‌شود و رویداد {{domxref("LanguageModel.contextoverflow_event", "contextoverflow")}} رخ می‌دهد.

برای تخمین اینکه یک درخواست جدید پیش از ارسال، چه تعداد توکن مصرف خواهد کرد، متد {{domxref("LanguageModel.measureContextUsage()")}} را فراخوانی کنید.

## مقدار

عددی که مصرف فعلی پنجرهٔ زمینه را بر حسب توکن نشان می‌دهد.

## مثال‌ها

### نظارت بر مصرف زمینه در طول گفتگو

این مثال پس از تکمیل یک درخواست در نشست، میزان مصرف زمینه را در کنسول می‌نویسد.

```js
const session = await LanguageModel.create();

await session.prompt("Tell me about the history of the internet.");

console.log(
  `Context used: ${session.contextUsage} / ${session.contextWindow} tokens`,
);
```

### هشدار زمانی که پنجرهٔ زمینه تقریباً پر است

مثال زیر از یک تابع استفاده می‌کند تا پیش از فراخوانی {{domxref("LanguageModel.prompt()", "prompt()")}} بررسی کند که فضای کافی در پنجرهٔ زمینه باقی مانده است. این تابع ابتدا فضای باقی‌مانده را محاسبه می‌کند و آن مقدار را به `measureContextUsage()` پاس می‌دهد. اگر `needed` کوچک‌تر یا مساوی `remaining` باشد، تابع `true` برمی‌گرداند و نشست ادامه می‌یابد.

```js
const promptText = "Let me ask you an interesting question...";

async function contextAvailable(promptText) {
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

- {{domxref("LanguageModel.contextWindow")}}
- {{domxref("LanguageModel.measureContextUsage()")}}
- رویداد {{domxref("LanguageModel.contextoverflow_event", "contextoverflow")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [Using the Prompt API](/en-US/docs/Web/API/Prompt_API/Using)