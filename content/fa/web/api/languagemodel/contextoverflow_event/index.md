---
title: "LanguageModel: contextoverflow event"
short-title: contextoverflow
slug: Web/API/LanguageModel/contextoverflow_event
page-type: web-api-event
browser-compat: api.LanguageModel.contextoverflow_event
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

رویداد **`contextoverflow`** روی یک نمونه از {{domxref("LanguageModel")}} رخ می‌دهد؛ زمانی که یک فراخوانی به {{domxref("LanguageModel.prompt()", "prompt()")}}، {{domxref("LanguageModel.promptStreaming()", "promptStreaming()")}} یا {{domxref("LanguageModel.append()", "append()")}} سبب شود {{domxref("LanguageModel.contextUsage", "contextUsage")}} جلسه از {{domxref("LanguageModel.contextWindow", "contextWindow")}} فراتر رود.

## سینتکس

نام رویداد را می‌توانید در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("contextoverflow", (event) => {})

oncontextoverflow = (event) => {}
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نمونه‌ها

### واکنش به سرریز context

کد زیر دو روش ایجاد یک شنونده رویداد (event listener) برای رویداد `contextoverflow` را نشان می‌دهد.

```js
const session = await LanguageModel.create();

session.addEventListener("contextoverflow", () => {
  console.warn("Context overflow detected.");
});
```

روش دیگر:

```js
const session = await LanguageModel.create();

session.oncontextoverflow = () => {
  console.warn(
    "The session's context window is full. " +
      "Consider cloning the session or starting a new one.",
  );
};
```

### بازنشانی جلسه هنگام سرریز

مثال زیر هنگام رخ دادن رویداد `contextoverflow` یک جلسه جدید ایجاد می‌کند.

```js
let session = await LanguageModel.create({
  initialPrompts: [{ role: "system", content: "You are a helpful assistant." }],
});

session.addEventListener("contextoverflow", async () => {
  console.log("Context full — creating a fresh session.");
  session.destroy();
  session = await LanguageModel.create({
    initialPrompts: [
      { role: "system", content: "You are a helpful assistant." },
    ],
  });
});

async function chat(userMessage) {
  const response = await session.prompt(userMessage);
  return response;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("LanguageModel.contextUsage")}}
- {{domxref("LanguageModel.contextWindow")}}
- {{domxref("LanguageModel.measureContextUsage()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)