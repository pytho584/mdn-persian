---
title: "LanguageModel: measureContextUsage() method"
short-title: measureContextUsage()
slug: Web/API/LanguageModel/measureContextUsage
page-type: web-api-instance-method
browser-compat: api.LanguageModel.measureContextUsage
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

متود **`measureContextUsage()`** از رابط {{domxref("LanguageModel")}} تخمین می‌زند که ورودی داده شده چند توکن از پنجره زمینه (context window) را مصرف می‌کند، بدون اینکه آن را به مدل ارسال کند یا وضعیت نشست (session) را تغییر دهد.

این امکان را به شما می‌دهد که قبل از تصمیم‌گیری برای ارسال یک ورودی، بررسی کنید که چه مقدار از پنجره زمینه را نیاز دارد. نتیجه را می‌توان با {{domxref("LanguageModel.contextWindow")}} و {{domxref("LanguageModel.contextUsage")}} مقایسه کرد تا مشخص شود که آیا ورودی در محدوده پنجره زمینه جای می‌گیرد یا خیر.

این ویژگی به‌ویژه برای برنامه‌های با زمینه طولانی مانند خلاصه‌سازی اسناد مفید است، جایی که ممکن است نیاز به تقسیم یا کوتاه کردن محتوا برای ماندن در محدوده پنجره زمینه داشته باشید.

## Syntax

```js-nolint
measureContextUsage(input)
measureContextUsage(input, options)
```

### پارامترها

- `input`
  - : محتوایی که به پنجره زمینه اضافه می‌شود. این می‌تواند یکی از موارد زیر باشد:
    - یک رشته — شکل مختصر یک پیام متنی واحد.
    - یک آرایه از اشیاء، که هر کدام یک پیام واحد در یک مکالمه با یک مدل زبانی را نشان می‌دهد. اشیاء ممکن است دارای ویژگی‌های زیر باشند:
      - `role`
        - : رشته‌ای که نشان‌دهنده دیدگاهی است که پیام از آن بیان می‌شود. باید یکی از موارد زیر باشد:
          - `system`
            - : یک دستورالعمل در سطح سیستم که رفتار کلی مدل را هدایت می‌کند. این باید اولین دستورالعملی باشد که به مدل ارسال می‌شود.
          - `user`
            - : پیامی از طرف کاربر که API باید به آن پاسخ دهد.
          - `assistant`
            - : ورودی‌ای که زمینه‌ای را برای دستیار هوش مصنوعی فراهم می‌کند، مانند شخصیت آن یا قالب پاسخ‌هایش. چنین پیام‌هایی عمدتاً برای ارائه زمینه/تاریخچه خدمت می‌کنند و نحوه پاسخ مدل را بیشتر شکل می‌دهند.
      - `content`
        - : یک رشته که یک prompt متنی را نشان می‌دهد، یا یک آرایه از اشیاء. هر شیء شامل ویژگی‌های زیر است:
          - `type`
            - : یک مقدار شمارشی که نوع محتوا را نشان می‌دهد. می‌تواند یکی از موارد زیر باشد:
              - `audio`
                - : محتوای صوتی.
              - `image`
                - : محتوای تصویری.
              - `text`
                - : محتوای متنی.
              - `tool-call`
                - : فراخوانی یک ابزار توسط مدل.
              - `tool-response`
                - : نتیجه یک فراخوانی ابزار.
          - `value`
            - : محتوای پیام. اگر `type` برابر `text` باشد، این همیشه یک رشته است. اگر `type` برابر `audio` یا `image` باشد، `value` می‌تواند یکی از چندین نوع شیء مختلف باشد؛ برای اطلاعات بیشتر به [چه نوع داده‌هایی پذیرفته می‌شوند؟](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) مراجعه کنید.
      - `prefix` {{optional_inline}}
        - : یک مقدار بولی که پیش‌فرض آن `false` است. وقتی `true` باشد، پیام به عنوان پیشوندی برای پاسخ تولید شده بعدی مدل در نظر گرفته می‌شود، نه یک نوبت کامل.
- `options` {{optional_inline}}
  - : گزینه‌هایی برای اندازه‌گیری استفاده از زمینه. ویژگی‌ها عبارتند از:
    - `responseConstraint`
      - : یک شیء با ساختار تعریف شده توسط [JSON Schema](https://json-schema.org/) که قالب دقیق خروجی مدل را مشخص می‌کند. وقتی ارائه شود و `omitResponseConstraintInput` برابر `false` باشد، هر پیام توصیف محدودیت تعریف شده توسط پیاده‌سازی در اندازه‌گیری گنجانده می‌شود.
    - `omitResponseConstraintInput`
      - : یک مقدار بولی؛ وقتی `true` باشد، پیام خودکار توصیف محدودیت از اندازه‌گیری حذف می‌شود.
    - `signal`
      - : یک {{domxref("AbortSignal")}} برای لغو عملیات.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{jsxref("Number")}} (عدد) حل می‌شود و نشان‌دهنده تعداد توکن‌های پنجره زمینه‌ای است که ورودی مصرف می‌کند.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : در صورت لغو عملیات از طریق گزینه `signal` پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورت مسدود شدن استفاده از متود توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - `role` یک پیام `assistant` باشد و `type` آن چیزی غیر از `text` باشد.
    - `type` یک پیام `text` باشد و `value` آن یک رشته نباشد.
    - متن ورودی یا خروجی به زبانی باشد که عامل کاربر (user agent) از آن برای prompting پشتیبانی نمی‌کند.
    - `type` یک پیام `image` یا `audio` باشد اما نوع در `expectedInputs` فهرست نشده باشد، یا `value` یک [نوع داده پذیرفته شده](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) نباشد.
- `SyntaxError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - هیچ پیامی در آرایه پیام‌ها گنجانده نشده باشد.
    - ویژگی `prefix` یک پیام روی `true` تنظیم شده باشد و:
      - `role` پیام `assistant` نباشد.
      - پیام آخرین مورد در آرایه پیام‌ها نباشد.
- `TypeError`
  - : در موارد زیر پرتاب می‌شود:
    - `omitResponseConstraintInput` `true` باشد اما `responseConstraint` ارائه نشده باشد.
    - `role` یک پیام `system` باشد اما اولین پیام ارسال شده به زمینه نباشد.

## مثال‌ها

### هشدار زمانی که زمینه تقریباً پر است

مثال زیر از یک تابع برای تأیید در دسترس بودن زمینه قبل از فراخوانی {{domxref("LanguageModel.prompt()")}} استفاده می‌کند. ابتدا زمینه باقی‌مانده را محاسبه کرده و آن مقدار را به `measureContextUsage()` ارسال می‌کند. اگر `needed` کمتر یا برابر با `remaining` باشد، `true` برمی‌گرداند و نشست ادامه می‌یابد.

```js
const promptText = "بگذارید یک سوال جالب از شما بپرسم...";

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
  console.warn("پرش از prompt: فضای کافی در پنجره زمینه باقی نمانده است.");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LanguageModel.contextUsage")}}
- {{domxref("LanguageModel.contextWindow")}}
- {{domxref("LanguageModel.append()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)