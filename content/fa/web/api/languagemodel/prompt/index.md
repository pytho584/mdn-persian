---
title: "LanguageModel: prompt() method"
short-title: prompt()
slug: Web/API/LanguageModel/prompt
page-type: web-api-instance-method
browser-compat: api.LanguageModel.prompt
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

متد **‎`prompt()`** از رابط {{domxref("LanguageModel")}} ورودی را به مدل زبانی می‌فرستد و یک {{jsxref("Promise")}} برمی‌گرداند که با پاسخ کامل مدل به‌صورت رشته (string) resolve می‌شود.

## سینتکس

```js-nolint
prompt(input)
prompt(input, options)
```

### پارامترها

- `input`
  - : محتوایی که باید با آن از مدل خواسته شود (prompt). این مقدار یکی از این دو است:
    - یک رشته — شکل کوتاه یک پیام متنی واحد.
    - یک آرایه از اشیا، که هر شیء یک پیام واحد در یک گفتگو با مدل زبانی را نشان می‌دهد. اشیا می‌توانند ویژگی‌های زیر را داشته باشند:
      - `role`
        - : رشته‌ای که دیدگاهِ بیان‌شده در پیام را نشان می‌دهد. باید یکی از این مقادیر باشد:
          - `system`
            - : یک دستورالعمل در سطح سیستم که رفتار کلی مدل را هدایت می‌کند. این باید نخستین دستورالعمل ارسال‌شده به مدل باشد.
          - `user`
            - : پیامی از طرف کاربر که API باید به آن پاسخ دهد.
          - `assistant`
            - : ورودی که زمینه (context) را برای دستیار هوش مصنوعی فراهم می‌کند، مانند شخصیت دستیار یا قالب پاسخ‌های آن. چنین پیام‌هایی عمدتاً برای فراهم‌کردن زمینه/تاریخچه و شکل‌دهی بیشتر به نحوهٔ پاسخ‌گویی مدل به کار می‌روند.
      - `content`
        - : رشته‌ای که یک prompt متنی را نشان می‌دهد، یا آرایه‌ای از اشیا. هر شیء ویژگی‌های زیر را دارد:
          - `type`
            - : یک مقدار شمارشی (enumerated) که نوع محتوا را نشان می‌دهد. می‌تواند یکی از این مقادیر باشد:
              - `audio`
                - : محتوای صوتی.
              - `image`
                - : محتوای تصویری.
              - `text`
                - : محتوای متنی.
              - `tool-call`
                - : فراخوانی ابزار (tool) که توسط مدل صادر شده است.
              - `tool-response`
                - : نتیجهٔ اجرای یک فراخوانی ابزار.
          - `value`
            - : محتوای پیام. اگر `type` برابر `text` باشد، این مقدار همیشه یک رشته است. اگر `type` برابر `audio` یا `image` باشد، `value` می‌تواند یکی از چند نوع شیء مختلف باشد؛ برای جزئیات بیشتر به [چه نوع داده‌هایی پذیرفته می‌شوند؟](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) مراجعه کنید.
      - `prefix` {{optional_inline}}
        - : یک مقدار بولی که پیش‌فرض آن `false` است. وقتی `true` باشد، پیام به‌جای یک نوبت کامل، به‌عنوان پیشوند (prefix) برای پاسخ بعدی تولیدشده توسط مدل در نظر گرفته می‌شود.
- `options` {{optional_inline}}
  - : گزینه‌های ساخت یک prompt. ویژگی‌های آن عبارت‌اند از:
    - `responseConstraint`
      - : شیئی که ساختار آن طبق [JSON Schema](https://json-schema.org/) تعریف شده است و قالب دقیقی را مشخص می‌کند که خروجی مدل باید در آن تحویل داده شود. وقتی این گزینه ارائه شود و `omitResponseConstraintInput` برابر `false` باشد، هر پیام توصیف‌کنندهٔ محدودیتِ تعریف‌شده توسط پیاده‌سازی در اندازه‌گیری (measurement) لحاظ می‌شود.
    - `omitResponseConstraintInput`
      - : یک مقدار بولی؛ وقتی `true` باشد، پیام خودکار توصیف‌کنندهٔ محدودیت از اندازه‌گیری حذف می‌شود.
    - `signal`
      - : یک {{domxref("AbortSignal")}} برای لغو عملیات.

### مقدار برگشتی

یک {{jsxref("Promise")}} که با یک {{jsxref("String")}} شامل پاسخ کامل مدل resolve می‌شود.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر عملیات از طریق گزینهٔ `signal` لغو شده باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر استفاده از این متد توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} مسدود شده باشد پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - نقش (`role`) یک پیام `assistant` باشد و `type` آن چیزی غیر از `text` باشد.
    - `type` یک پیام `text` باشد و `value` آن رشته نباشد.
    - متن ورودی یا خروجی به زبانی باشد که عامل کاربر (user agent) برای ارائهٔ prompt پشتیبانی نمی‌کند.
    - `type` یک پیام `image` یا `audio` باشد اما این نوع در `expectedInputs` فهرست نشده باشد، یا `value` یک [نوع دادهٔ پذیرفته‌شده](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) نباشد.
- `OperationError` {{domxref("DOMException")}}
  - : اگر prompt به هر دلیل دیگری که در سایر انواع استثنا ذکر نشده شکست بخورد، پرتاب می‌شود.
- `QuotaExceededError` {{domxref("DOMException")}}
  - : اگر prompt باعث شود استفاده از زمینهٔ نشست (context) از {{domxref("LanguageModel.contextWindow")}} مدل فراتر رود، پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - هیچ پیامی در آرایهٔ messages گنجانده نشده باشد.
    - ویژگی `prefix` یک پیام برابر `true` باشد و:
      - نقش (`role`) آن پیام `assistant` نباشد.
      - آن پیام آخرین آیتم در آرایهٔ messages نباشد.
- `TypeError`
  - : در موارد زیر پرتاب می‌شود:
    - `omitResponseConstraintInput` برابر `true` باشد اما `responseConstraint` ارائه نشده باشد.
    - نقش (`role`) یک پیام `system` باشد اما نخستین پیام ارسال‌شده به زمینه نباشد.

## توضیحات

متد `prompt()` سازوکار اصلی تعامل با یک نشست مدل زبانی است. این متد ورودی ارائه‌شده را به پنجرهٔ زمینه (context window) اضافه می‌کند و پاسخی تولید می‌کند. کل پاسخ هنگام تکمیل تولید، بافر شده و به‌صورت یک رشتهٔ واحد بازگردانده می‌شود.

برای پاسخ‌های طولانی یا موارد استفادهٔ جریانی (streaming)، به‌جای آن از {{domxref("LanguageModel.promptStreaming()")}} استفاده کنید تا پاسخ به‌صورت تدریجی دریافت شود. برای افزودن محتوا به پنجرهٔ زمینه بدون تولید پاسخ، از {{domxref("LanguageModel.append()")}} استفاده کنید.

هر بار فراخوانی `prompt()` به زمینهٔ نشست اضافه می‌کند. برای اینکه از یک وضعیت مشخص بدون تأثیرگذاری بر نشست اصلی شاخهٔ جدیدی بسازید، {{domxref("LanguageModel.clone()")}} را فراخوانی کنید.

## مثال‌ها

### مثال پایهٔ متنی

این مثال کاربرد پایه‌ای `prompt()` را با یک ورودی متنی واحد از کاربر نشان می‌دهد.

```js
const session = await LanguageModel.create();
const response = await session.prompt(
  "Summarize the water cycle in one paragraph.",
);
console.log(response);
```

همچنین ببینید: [استفاده از Prompt API > ارائهٔ prompt به مدل](/en-US/docs/Web/API/Prompt_API/Using#prompting_the_model).

### گفتگو با چند نوبت

```js
const session = await LanguageModel.create();

const reply1 = await session.prompt("My name is Alex.");
console.log(reply1); // "Nice to meet you, Alex!"

const reply2 = await session.prompt("What's my name?");
console.log(reply2); // "Your name is Alex."
```

### خروجی JSON مقید

مثال زیر نشان می‌دهد که چگونه JSON را به گزینهٔ `responseConstraint` بدهید تا مشخص کنید می‌خواهید فراخوانی `prompt()` یک آرایه برگرداند.

```js
const session = await LanguageModel.create();
const raw = await session.prompt("Name three planets in our solar system.", {
  responseConstraint: {
    type: "object",
    properties: {
      planets: {
        type: "array",
        items: { type: "string" },
      },
    },
    required: ["planets"],
  },
});

const { planets } = JSON.parse(raw);
console.log(planets); // ["Mercury", "Venus", "Earth"]
```

همچنین ببینید: [افزودن زمینه با ورودی‌های prompt اولیه و مداوم > افزودن محدودیت‌های پاسخ](/en-US/docs/Web/API/Prompt_API/Adding_context#adding_response_constraints).

### لغو یک prompt

مثال زیر نشان می‌دهد چگونه به کاربر اجازه دهید با یک دکمه، prompt را لغو کند. این کار با ایجاد یک {{domxref("AbortController")}} انجام می‌شود. متد `abort()` آن از طریق پردازندهٔ رویداد `click` یک دکمه قابل فراخوانی است. برای اینکه این کار درست عمل کند، ارجاعی از ویژگی `signal` کنترلر باید به `prompt()` ارسال شود.

```js
const controller = new AbortController();

// Select your cancel button from the DOM
const cancelButton = document.querySelector("#btn-cancel");

// Trigger the abort when the user clicks the button
cancelButton.addEventListener("click", () => {
  controller.abort();
});

try {
  const response = await session.prompt("write a very long story.", {
    signal: controller.signal,
  });
  console.log(response);
} catch (err) {
  if (err.name === "AbortError") {
    console.log("prompt was cancelled.");
  } else {
    console.error("An unexpected error occurred:", err);
  }
}
```

همچنین ببینید: [استفاده از Prompt API > لغو عملیات‌ها و نابود کردن نمونه‌ها](/en-US/docs/Web/API/Prompt_API/Using#cancelling_operations_and_destroying_instances).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LanguageModel.promptStreaming()")}}
- {{domxref("LanguageModel.append()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)
- [افزودن زمینه با ورودی‌های prompt اولیه و مداوم](/en-US/docs/Web/API/Prompt_API/Adding_context)