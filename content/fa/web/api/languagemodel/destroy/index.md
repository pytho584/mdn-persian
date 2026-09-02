---
title: "LanguageModel: destroy() method"
short-title: destroy()
slug: Web/API/LanguageModel/destroy
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LanguageModel.destroy
---

{{APIRef("Prompt API")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`destroy()`** از رابط {{domxref("LanguageModel")}}، منابع تخصیص‌داده‌شده به نمونه‌ای از `LanguageModel` را که روی آن فراخوانی می‌شود آزاد می‌کند و هر فعالیت بیشتری روی آن را متوقف می‌سازد. هر فراخوانی متدی که روی این `LanguageModel` در حال انجام باشد یا پس از آن انجام شود، با یک `AbortError` رد خواهد شد.

اگر دیگر از اشیاء `LanguageModel` استفاده نمی‌کنید، منطقی است که آن‌ها را از بین ببرید؛ زیرا مدیریت آن‌ها منابع قابل توجهی را اشغال می‌کند.

## سینتکس

```js-nolint
destroy()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر استفاده از این متد توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} مسدود شده باشد، این استثنا پرتاب می‌شود.

## مثال‌ها

### استفاده‌ی پایه از `destroy()`

```js
const session = await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});

// ...

session.destroy();
```

همچنین ببینید: [استفاده از Prompt API > لغو عملیات‌ها و از بین بردن نمونه‌ها](/en-US/docs/Web/API/Prompt_API/Using#cancelling_operations_and_destroying_instances).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)