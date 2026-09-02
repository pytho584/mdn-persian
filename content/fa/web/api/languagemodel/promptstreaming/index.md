---
title: "LanguageModel: متد promptStreaming()"
short-title: promptStreaming()
slug: Web/API/LanguageModel/promptStreaming
page-type: web-api-instance-method
browser-compat: api.LanguageModel.promptStreaming
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

متد **`promptStreaming()`** از رابط {{domxref("LanguageModel")}} ورودی را به مدل زبانی ارسال می‌کند و یک {{domxref("ReadableStream")}} برمی‌گرداند که پاسخ مدل را به صورت تدریجی و در حین تولید تحویل می‌دهد.

این روش برای نمایش تدریجی پاسخ‌ها به کاربران در خروجی‌هایی که زمان زیادی طول می‌کشند، یا برای هر سناریویی که باید تأخیر درک شده کاهش یابد، مفید است. استریم را با استفاده از `for await...of` یا با متصل کردن یک خواننده از طریق {{domxref("ReadableStream.getReader()")}} مصرف کنید.

## نحو

```js-nolint
promptStreaming(input)
promptStreaming(input, options)
```

### پارامترها

- `input`
  - : محتوایی که برای درخواست به مدل ارسال می‌شود. این مقدار یکی از موارد زیر است:
    - یک رشته (string) — صورت خلاصه‌ای از یک پیام متنی واحد.
    - یک آرایه از اشیاء، که هر کدام نمایانگر یک پیام واحد در یک مکالمه با مدل زبانی هستند.
      اشیاء می‌توانند ویژگی‌های زیر را داشته باشند:
      - `role`
        - : رشته‌ای که نشان‌دهنده دیدگاه پیام است. باید یکی از موارد زیر باشد:
          - `system`
            - : یک دستورالعمل در سطح سیستم که رفتار کلی مدل را هدایت می‌کند. این باید اولین دستورالعمل ارسال‌شده به مدل باشد.
          - `user`
            - : پیامی از سوی کاربر که API باید به آن پاسخ دهد.
          - `assistant`
            - : ورودی که زمینه‌ای را برای دستیار هوش مصنوعی فراهم می‌کند، مانند شخصیت یا قالب پاسخ‌های آن. چنین پیام‌هایی عمدتاً برای ارائه زمینه/تاریخچه و شکل‌دهی بیشتر به نحوه پاسخ مدل خدمت می‌کنند.
      - `content`
        - : یک رشته که نمایانگر یک درخواست متنی است، یا یک آرایه از اشیاء. هر شیء شامل ویژگی‌های زیر است:
          - `type`
            - : یک مقدار شمارشی که نوع محتوا را نشان می‌دهد. می‌تواند یکی از موارد زیر باشد:
              - `audio`
                - : محتوای صوتی.
              - `image`
                - : محتوای تصویری.
              - `text`
                - : محتوای متنی.
              - `tool-call`
                - : فراخوانی ابزار توسط مدل.
              - `tool-response`
                - : نتیجه یک فراخوانی ابزار.
          - `value`
            - : محتوای پیام. اگر `type` برابر `text` باشد، این مقدار همیشه یک رشته است. اگر `type` برابر `audio` یا `image` باشد، `value` می‌تواند یکی از انواع مختلف شیء باشد؛ به [چه انواع داده‌ای پذیرفته می‌شوند؟](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) مراجعه کنید.
      - `prefix` {{optional_inline}}
        - : یک مقدار بولی، پیش‌فرض `false`. وقتی `true` باشد، پیام به عنوان پیشوندی برای پاسخ بعدی مدل در نظر گرفته می‌شود، نه یک نوبت کامل.
- `options` {{optional_inline}}
  - : گزینه‌هایی برای ایجاد یک درخواست. ویژگی‌ها عبارتند از:
    - `responseConstraint`
      - : یک شیء که از ساختار تعریف‌شده توسط [JSON Schema](https://json-schema.org/) پیروی می‌کند و قالب دقیق خروجی مدل را مشخص می‌کند. وقتی ارائه شود و `omitResponseConstraintInput` برابر `false` باشد، هر پیام توصیف محدودیت تعریف‌شده توسط پیاده‌سازی در اندازه‌گیری گنجانده می‌شود.
    - `omitResponseConstraintInput`
      - : یک مقدار بولی؛ وقتی `true` باشد، پیام خودکار توصیف محدودیت از اندازه‌گیری حذف می‌شود.
    - `signal`
      - : یک {{domxref("AbortSignal")}} برای لغو عملیات.

### مقدار بازگشتی

یک {{domxref("ReadableStream")}} از بخش‌های {{jsxref("String")}}. هر بخش نمایانگر بخشی از پاسخ مدل در حین تولید است. استریم با اتمام تولید بسته می‌شود.

### استثناها

خطاها به عنوان خطاهای استریم (stream errors) ظاهر می‌شوند، نه به عنوان وعده‌های رد شده. مصرف‌کنندگان باید با استفاده از مکانیزم‌های استاندارد مدیریت خطای استریم، خطاها را مدیریت کنند.

- `AbortError` {{domxref("DOMException")}}
  - : اگر عملیات از طریق گزینه `signal` لغو شود، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر استفاده از این متد توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} مسدود شده باشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - `role` یک پیام `assistant` باشد و `type` آن چیزی غیر از `text` باشد.
    - `type` یک پیام `text` باشد و `value` آن یک رشته نباشد.
    - متن ورودی یا خروجی به زبانی باشد که عامل کاربر (user agent) برای درخواست از مدل پشتیبانی نمی‌کند.
    - `type` یک پیام `image` یا `audio` باشد اما این نوع در `expectedInputs` لیست نشده باشد، یا `value` یک [نوع داده پذیرفته‌شده](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) نباشد.
- `OperationError` {{domxref("DOMException")}}
  - : اگر درخواست به هر دلیل دیگری غیر از موارد ذکر شده در سایر انواع استثنا شکست بخورد، پرتاب می‌شود.
- `QuotaExceededError` {{domxref("DOMException")}}
  - : اگر درخواست باعث شود استفاده از زمینه جلسه از {{domxref("LanguageModel.contextWindow")}} مدل فراتر رود، پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - هیچ پیامی در آرایه پیام‌ها گنجانده نشده باشد.
    - ویژگی `prefix` یک پیام روی `true` تنظیم شده باشد و:
      - `role` آن پیام `assistant` نباشد.
      - آن پیام آخرین آیتم در آرایه پیام‌ها نباشد.
- `TypeError`
  - : در موارد زیر پرتاب می‌شود:
    - `omitResponseConstraintInput` برابر `true` باشد اما `responseConstraint` ارائه نشده باشد.
    - `role` یک پیام `system` باشد اما اولین پیام ارسال‌شده به زمینه نباشد.

## توضیحات

متد `promptStreaming()` ورودی ارائه‌شده را به پنجره زمینه (context window) اضافه کرده و یک پاسخ تولید می‌کند. کل پاسخ به صورت تدریجی به عنوان یک {{domxref("ReadableStream")}} دریافت می‌شود.

برای دریافت پاسخ به صورت یک رشته کامل، از {{domxref("LanguageModel.prompt()")}} استفاده کنید. برای افزودن محتوا به پنجره زمینه بدون تولید پاسخ، از {{domxref("LanguageModel.append()")}} استفاده کنید.

هر بار فراخوانی `promptStreaming()` به زمینه جلسه اضافه می‌کند. برای انشعاب از یک حالت خاص بدون تأثیر بر جلسه اصلی، {{domxref("LanguageModel.clone()")}} را فراخوانی کنید.

## مثال‌ها

### استریم پاسخ به صفحه

این مثال بخش‌های حاصل از فراخوانی `promptStreaming()` را هنگام رسیدن به صورت تکه‌تکه در صفحه می‌نویسد.

```js
const session = await LanguageModel.create();
const output = document.querySelector("#output");

const stream = session.promptStreaming("یک شعر کوتاه درباره اقیانوس بنویس.");

for await (const chunk of stream) {
  output.textContent += chunk;
}
```

همچنین به [استفاده از Prompt API > مثال کامل استریم](/en-US/docs/Web/API/Prompt_API/Using#complete_streaming_example) مراجعه کنید.

### استریم با سیگنال لغو

این مثال نحوه استفاده از {{domxref("AbortController")}} را با `promptStreaming()` نشان می‌دهد.

```js
const controller = new AbortController();
document
  .querySelector("#stop")
  .addEventListener("click", () => controller.abort());

const stream = session.promptStreaming("یک داستان بلند برایم بگو.", {
  signal: controller.signal,
});

try {
  for await (const chunk of stream) {
    output.textContent += chunk;
  }
} catch (err) {
  if (err.name === "AbortError") {
    console.log("استریم توسط کاربر متوقف شد.");
  }
}
```

### جمع‌آوری بخش‌های استریم شده در یک رشته واحد

در این مثال، بخش‌های یک {{domxref("ReadableStream")}} قبل از نوشتن کل استریم جمع‌آوری می‌شوند.

```js
const session = await LanguageModel.create();
const stream = session.promptStreaming("درهم‌تنیدگی کوانتومی را توضیح بده.");
const chunks = [];

for await (const chunk of stream) {
  chunks.push(chunk);
}

const fullResponse = chunks.join("");
console.log(fullResponse);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LanguageModel.prompt()")}}
- {{domxref("ReadableStream")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)
- [افزودن زمینه با ورودی‌های اولیه و مداوم درخواست](/en-US/docs/Web/API/Prompt_API/Adding_context)