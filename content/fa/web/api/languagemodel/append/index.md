---
title: "LanguageModel: append() method"
short-title: append()
slug: Web/API/LanguageModel/append
page-type: web-api-instance-method
browser-compat: api.LanguageModel.append
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

متد **`append()`** در رابط {{domxref("LanguageModel")}} محتوایی را به پنجرهٔ زمینهٔ نشست اضافه می‌کند بدون اینکه پاسخی از مدل تولید کند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که پس از بارگذاری موفقیت‌آمیز محتوا در زمینه، resolve می‌شود. از این متد برای پیش‌بارگذاری زمینه پیش از پرسیدن سؤال از مدل استفاده کنید.

زمینه می‌تواند یک سند، گفت‌وگو، تاریخچه یا اطلاعات پس‌زمینه باشد. می‌توانید متد `append()` را در هر نقطه‌ای از طول عمر نشست فراخوانی کنید.

## سینتکس

```js-nolint
append(input)
append(input, options)
```

### پارامترها

- `input`
  - : محتوایی که به پنجرهٔ زمینه اضافه می‌شود. این محتوا یکی از این دو حالت است:
    - یک رشته — شکل کوتاه‌شده برای یک پیام متنی واحد.
    - آرایه‌ای از اشیا که هر کدام نمایانگر یک پیام واحد در گفت‌وگو با یک مدل زبانی است.
      اشیا می‌توانند ویژگی‌های زیر را داشته باشند:
      - `role`
        - : رشته‌ای که دیدگاه بیان‌شده در پیام را مشخص می‌کند. باید یکی از موارد زیر باشد:
          - `system`
            - : دستوری در سطح سیستم که رفتار کلی مدل را هدایت می‌کند. این دستور باید اولین دستوری باشد که به مدل ارسال می‌شود.
          - `user`
            - : پیامی از کاربر که API باید به آن پاسخ دهد.
          - `assistant`
            - : ورودی‌ای که زمینه را برای دستیار هوش مصنوعی فراهم می‌کند؛ مانند شخصیت آن یا قالب پاسخ‌های آن. چنین پیام‌هایی عمدتاً برای فراهم‌کردن زمینه/تاریخچه به کار می‌روند و به شکل‌دهی بیشتر پاسخ مدل کمک می‌کنند.
      - `content`
        - : رشته‌ای که یک درخواست متنی (textual prompt) را نشان می‌دهد، یا آرایه‌ای از اشیا. هر شیء شامل ویژگی‌های زیر است:
          - `type`
            - : یک مقدار شمارشی که نوع محتوا را مشخص می‌کند. این مقدار می‌تواند یکی از موارد زیر باشد:
              - `audio`
                - : محتوای صوتی.
              - `image`
                - : محتوای تصویری.
              - `text`
                - : محتوای متنی.
              - `tool-call`
                - : فراخوانی ابزاری که توسط مدل صادر شده است.
              - `tool-response`
                - : نتیجهٔ فراخوانی یک ابزار.
          - `value`
            - : محتوای پیام. اگر `type` برابر با `text` باشد، این مقدار همیشه یک رشته است. اگر `type` برابر با `audio` یا `image` باشد، `value` می‌تواند یکی از چند نوع شیء مختلف باشد؛ برای جزئیات بیشتر به [چه نوع داده‌هایی پذیرفته می‌شوند؟](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) مراجعه کنید.
      - `prefix` {{optional_inline}}
        - : یک مقدار بولی که پیش‌فرض آن `false` است. وقتی `true` باشد، این پیام به‌جای یک نوبت کامل، به‌عنوان پیشوندی برای پاسخ تولیدشدهٔ بعدی مدل در نظر گرفته می‌شود.
- `options` {{optional_inline}}
  - : شیئی نمایانگر گزینه‌هایی که می‌توان ارسال کرد. ویژگی‌های آن عبارت‌اند از:
    - `signal`
      - : یک {{domxref("AbortSignal")}} برای لغو عملیات افزودن.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که وقتی محتوا از پیش در پنجرهٔ زمینه قرار گرفت، با `undefined` resolve می‌شود و در صورت شکست با یکی از مقادیر استثنایی زیر reject می‌شود.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر عملیات از طریق گزینهٔ `signal` لغو شده باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر استفاده از این متد توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} در {{httpheader("Permissions-Policy")}} مسدود شده باشد پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که:
    - نقش (role) یک پیام `assistant` باشد و نوع (`type`) آن چیزی غیر از `text` باشد.
    - نوع یک پیام `text` باشد و `value` آن یک رشته نباشد.
    - متن ورودی یا خروجی به زبانی باشد که عامل کاربر (user agent) برای ارسال prompt از آن پشتیبانی نمی‌کند.
    - نوع یک پیام `image` یا `audio` باشد، اما این نوع در `expectedInputs` فهرست نشده باشد، یا `value` یکی از [انواع دادهٔ پذیرفته‌شده](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) نباشد.
- `OperationError` {{domxref("DOMException")}}
  - : اگر پیش‌پرکردن به هر دلیل دیگری غیر از موارد ذکرشده در سایر انواع استثنا شکست بخورد پرتاب می‌شود.
- `QuotaExceededError` {{domxref("DOMException")}}
  - : اگر افزودن `input` باعث شود استفاده از زمینهٔ نشست از {{domxref("LanguageModel.contextWindow")}} مدل فراتر رود پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که:
    - هیچ پیامی در آرایهٔ پیام‌ها وجود نداشته باشد.
    - ویژگی `prefix` یک پیام `true` باشد و:
      - نقش (role) آن پیام `assistant` نباشد.
      - آن پیام آخرین آیتم در آرایهٔ پیام‌ها نباشد.
- `TypeError` {{domxref("DOMException")}}
  - : اگر نقش (role) یک پیام `system` باشد اما این پیام نخستین پیامی نباشد که به زمینه ارسال شده است.

## مثال‌ها

همچنین ببینید [افزودن زمینه با ورودی‌های پرامپت آغازین و پیوسته > افزودن پیام‌های بیشتر به زمینه](/en-US/docs/Web/API/Prompt_API/Adding_context#appending_extra_messages_to_the_context).

### افزودن زمینه پیش از پرسیدن از مدل

این مثال نشان می‌دهد که چگونه می‌توان پیش از فراخوانی `prompt()` زمینه‌ای برای نقش کاربر اضافه کرد. توجه کنید که در این حالت می‌توانیم فقط ورودی متنی (`documentText`) را مشخص کنیم، زیرا `user` نقش پیش‌فرض است.

```js
const documentText = "This is my important essay...";
const session = await LanguageModel.create();

// Preload the document text into context
await session.append(documentText);

// Now ask questions about the document
const summary = await session.prompt(
  "Summarize the key points of this document.",
);
console.log(summary);
```

### افزودن زمینه با سیگنال انصراف

یک سیگنال انصراف به شما امکان می‌دهد عملیات افزودن را لغو کنید. مثال زیر یک {{domxref("AbortSignal")}} را به عضو `signal` ارسال می‌کند و پس از ۳ ثانیه متد `abort()` کنترل‌کننده را فراخوانی می‌کند.

```js
const controller = new AbortController();
setTimeout(() => controller.abort(), 3000);

try {
  await session.append(
    "Here is some background context for future questions.",
    {
      signal: controller.signal,
    },
  );
  console.log("Context appended successfully.");
} catch (err) {
  if (err.name === "AbortError") {
    console.log("Append was aborted.");
  }
}
```

### بررسی میزان استفاده از زمینه پس از افزودن

کد زیر نشان می‌دهد که چگونه می‌توان پس از افزودن حجم زیادی از زمینه، تعداد توکن‌های استفاده‌شده را در خروجی ثبت کرد.

```js
const largeDocument = "This is my large body of text...";
const session = await LanguageModel.create();
await session.append(largeDocument);

console.log(
  `Context used: ${session.contextUsage} / ${session.contextWindow} tokens`,
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("LanguageModel.prompt()")}}
- {{domxref("LanguageModel.measureContextUsage()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [Using the Prompt API](/en-US/docs/Web/API/Prompt_API/Using)
- [Adding context with initial and ongoing prompt inputs](/en-US/docs/Web/API/Prompt_API/Adding_context)