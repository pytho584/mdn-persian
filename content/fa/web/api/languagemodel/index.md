---
title: "LanguageModel"
slug: Web/API/LanguageModel
page-type: web-api-interface
browser-compat: api.LanguageModel
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

رابط **`LanguageModel`** از [API Prompt](/en-US/docs/Web/API/Prompt_API) یک نشست (session) با یک مدل زبانی ارائه‌شده توسط مرورگر را نشان می‌دهد. این رابط متدهای ایستا برای ایجاد نشست‌ها و بررسی در دسترس بودن، و همچنین متدهای نمونه برای ارائه درخواست به مدل، افزودن زمینه (context) و مدیریت پنجره زمینه را ارائه می‌دهد.

نمونه‌های `LanguageModel` را نمی‌توان مستقیماً ساخت. در عوض، از متد ایستا {{domxref("LanguageModel.create_static", "LanguageModel.create()")}} استفاده کنید.

{{InheritanceDiagram}}

## متدهای ایستا

- {{domxref("LanguageModel.availability_static", "LanguageModel.availability()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با یک مقدار شمارشی حل می‌شود و نشان می‌دهد که آیا مدل زبانی برای گزینه‌های داده شده در دسترس است یا خیر.
- {{domxref("LanguageModel.create_static", "LanguageModel.create()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با یک نشست جدید `LanguageModel` حل می‌شود و در صورت نیاز داده‌های مدل را دانلود می‌کند.

## متدهای نمونه

- {{domxref("LanguageModel.append()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که وقتی ورودی داده شده به پنجره زمینه نشست اضافه شود، بدون تولید پاسخ، حل می‌شود.
- {{domxref("LanguageModel.clone()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با یک نشست جدید `LanguageModel` که کپی نشستی است که روی آن فراخوانی شده، شامل تمام زمینه، حل می‌شود.
- {{domxref("LanguageModel.destroy()")}} {{experimental_inline}}
  - : منابع اختصاص داده شده به نمونه `LanguageModel` که روی آن فراخوانی شده را آزاد می‌کند و هر فعالیت بیشتر روی آن را متوقف می‌کند.
- {{domxref("LanguageModel.measureContextUsage()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با تعداد توکن‌های پنجره زمینه که ورودی داده شده در صورت استفاده در عملیاتی مانند `prompt()` یا `append()` مصرف می‌کند، حل می‌شود.
- {{domxref("LanguageModel.prompt()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با پاسخ کامل مدل به ورودی داده شده حل می‌شود.
- {{domxref("LanguageModel.promptStreaming()")}}
  - : یک {{domxref("ReadableStream")}} بازمی‌گرداند که پاسخ مدل به ورودی داده شده را به‌صورت جریانی در حین تولید، پخش می‌کند.

## ویژگی‌های نمونه

- {{domxref("LanguageModel.contextUsage")}} {{ReadOnlyInline}}
  - : تعداد توکن‌های پنجره زمینه که در حال حاضر توسط این نشست مصرف شده است را بازمی‌گرداند.
- {{domxref("LanguageModel.contextWindow")}} {{ReadOnlyInline}}
  - : اندازه کل پنجره زمینه در دسترس برای این نشست را بر حسب توکن بازمی‌گرداند.

## رویدادها

- {{domxref("LanguageModel.contextoverflow_event", "contextoverflow")}}
  - : زمانی رخ می‌دهد که یک فراخوانی `prompt()`، `promptStreaming()` یا `append()` از اندازه پنجره زمینه فراتر رود.

## مثال‌ها

### ایجاد یک نشست و ارائه درخواست به مدل

این مثال ابتدا {{domxref("LanguageModel.create_static", "create()")}} را فراخوانی می‌کند تا یک نشست جدید دریافت کند. این مشخص می‌کند که مدل زبانی نقش `"system"` را اتخاذ کند و نحوه رفتار آن را تعریف می‌کند. توجه داشته باشید که مثال از `await` استفاده می‌کند زیرا `create()` یک {{jsxref("Promise")}} بازمی‌گرداند. اگر مدل نیاز به دانلود داشته باشد، حل شدن این Promise ممکن است مدتی طول بکشد.

پس از ایجاد نشست، مثال {{domxref("LanguageModel.prompt()", "prompt()")}} را فراخوانی می‌کند تا یک سوال مشخص بپرسد.

```js
const session = await LanguageModel.create({
  initialPrompts: [
    {
      role: "system",
      content: "You are a helpful assistant.",
    },
  ],
});

const response = await session.prompt("What is the capital of France?");
console.log(response); // "The capital of France is Paris."
```

### پخش جریانی پاسخ

این مثال {{domxref("LanguageModel.promptStreaming()", "promptStreaming()")}} را فراخوانی می‌کند تا یک نمونه از {{domxref("ReadableStream")}} دریافت کند و آن را به صورت تکه‌تکه در کنسول می‌نویسد.

```js
const session = await LanguageModel.create();
const readableStream = session.promptStreaming("Tell me a short story.");

for await (const chunk of readableStream) {
  console.log(chunk);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Prompt API](/en-US/docs/Web/API/Prompt_API)