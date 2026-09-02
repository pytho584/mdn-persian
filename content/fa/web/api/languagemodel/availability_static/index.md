---
title: "LanguageModel: availability() static method"
---

---
title: "LanguageModel: availability() static method"
short-title: availability()
slug: Web/API/LanguageModel/availability_static
page-type: web-api-static-method
browser-compat: api.LanguageModel.availability_static
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

متد ایستای **`availability()`** در رابط {{domxref("LanguageModel")}} یک شناسه وضعیت برمی‌گرداند که نشان می‌دهد آیا مدل زبانی مرورگر مجموعه‌ای معین از گزینه‌های پیکربندی را پشتیبانی می‌کند یا نه، بدون اینکه نشستی ایجاد کند یا دانلودی را آغاز کند.

برای تعیین اینکه آیا پیکربندی موردنظر پشتیبانی می‌شود یا نه، قبل از فراخوانی {{domxref("LanguageModel.create_static", "LanguageModel.create()")}} از `availability()` استفاده کنید. این کار از ایجاد نشستی که فقط برای شکست خوردن ایجاد شده است جلوگیری می‌کند و به شما امکان می‌دهد وقتی پیکربندی پشتیبانی نمی‌شود، یک راهکار جایگزین معنادار به کاربران ارائه دهید.

## Syntax

```js-nolint
LanguageModel.availability()
LanguageModel.availability(options)
```

### Parameters

- `options` {{optional_inline}}
  - : شیئی که مجموعه پایه گزینه‌های مورد استفاده هنگام بررسی پشتیبانی مدل زبانی را نشان می‌دهد.
    ویژگی‌ها عبارت‌اند از:

    - `expectedInputs` {{optional_inline}}
      - : آرایه‌ای از اشیاء که نشان‌دهنده انواع ورودی و زبان‌های مورد نیاز است.
        هر شیء می‌تواند ویژگی‌های زیر را شامل شود:

        - `type`
          - : یک مقدار شمارشی که نوع محتوا را نشان می‌دهد. باید یکی از موارد زیر باشد:
            - `text`
              - : محتوای متن ساده.
            - `image`
              - : محتوای تصویر.
            - `audio`
              - : محتوای صوتی.
            - `tool-call`
              - : فراخوانی ابزار که توسط مدل صادر شده است.
            - `tool-response`
              - : نتیجه یک فراخوانی ابزار.
        - `languages` {{optional_inline}}
          - : آرایه‌ای از رشته‌ها حاوی برچسب‌های زبان [BCP 47](https://www.rfc-editor.org/rfc/rfc5646) (برای مثال، `en`، `fr`، `ja`) که زبان‌هایی را نشان می‌دهد که انتظار می‌رود نشست آن‌ها را مدیریت کند. عامل کاربر از این فهرست برای تعیین اینکه آیا مدل از زبان‌های مشخص‌شده پشتیبانی می‌کند یا نه استفاده می‌کند.
    - `expectedOutputs`
      - : آرایه‌ای از اشیاء که نشان‌دهنده انواع خروجی و زبان‌های مورد نیاز است.
        هر شیء می‌تواند ویژگی‌های زیر را شامل شود:

        - `type`
          - : یک مقدار شمارشی که نوع محتوا را نشان می‌دهد. باید یکی از موارد زیر باشد:
            - `text`
              - : محتوای متنی.
            - `image`
              - : محتوای تصویر.
            - `audio`
              - : محتوای صوتی.
            - `tool-call`
              - : فراخوانی ابزار که توسط مدل صادر شده است.
            - `tool-response`
              - : نتیجه یک فراخوانی ابزار.
        - `languages` {{optional_inline}}
          - : آرایه‌ای از رشته‌ها حاوی برچسب‌های زبان [BCP 47](https://www.rfc-editor.org/rfc/rfc5646) (برای مثال، `en`، `fr`، `ja`) که انتظار می‌رود نشست آن‌ها را خروجی دهد.
    - `tools`
      - : آرایه‌ای از اشیاء که ابزارهای در دسترس هوش مصنوعی را نشان می‌دهد.
        هر شیء می‌تواند ویژگی‌های زیر را شامل شود:

        - `name`
          - : رشته‌ای که به ابزار یک نام یکتا می‌دهد؛ مدل هنگام صدور فراخوانی ابزار از این نام برای ارجاع به ابزار استفاده می‌کند.
        - `description`
          - : رشته‌ای که توصیف می‌کند ابزار چه کاری انجام می‌دهد.
            مدل از این توصیف برای تصمیم‌گیری در مورد زمان و اینکه آیا ابزار را فراخوانی کند استفاده می‌کند.
        - `inputSchema`
          - : شیئی حاوی یک [JSON Schema](https://json-schema.org/) که پارامترهای ورودی ابزار را توصیف می‌کند.
            مدل از این schema برای ساخت آرگومان‌هایی که به تابع `execute` ابزار منتقل می‌کند استفاده می‌کند.
        - `execute`
          - : یک تابع بازفراخوانی (callback) که عامل کاربر هنگام فراخوانی این ابزار توسط مدل، آن را فراخوانی می‌کند.
            این تابع می‌تواند هر آرگومان مناسبی را که مدل ارائه کرده است دریافت کند و یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{jsxref("String")}} نشان‌دهنده نتیجه ابزار، حل می‌شود.

### Return value

یک {{jsxref("Promise")}} که با یکی از مقادیر زیر حل می‌شود.

- `available`
  - : مدل با گزینه‌های داده‌شده آماده استفاده است.
- `downloadable`
  - : مدل می‌تواند گزینه‌های داده‌شده را پشتیبانی کند، اما برای این کار باید داده‌های اضافی دانلود کند. دانلود هنوز آغاز نشده است.
- `downloading`
  - : مدل می‌تواند گزینه‌های داده‌شده را با یک دانلود داده اضافی پشتیبانی کند. دانلود در حال حاضر در جریان است.
- `unavailable`
  - : مدل نمی‌تواند گزینه‌های داده‌شده را پشتیبانی کند، یا عامل کاربر نمی‌تواند در دسترس بودن را تعیین کند، برای مثال به دلیل خطای [فعال‌سازی گذرا](/en-US/docs/Glossary/Transient_activation). در این صورت، فراخواننده باید دوباره تلاش کند یا به یک پیاده‌سازی جایگزین برگردد.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند فراخواننده کاملاً فعال نباشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر استفاده از این متد توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} مسدود شده باشد پرتاب می‌شود.

## Examples

همچنین ببینید [استفاده از Prompt API > بررسی پشتیبانی پیکربندی](/en-US/docs/Web/API/Prompt_API/Using#checking_configuration_support) و [نمونه کامل](/en-US/docs/Web/API/Prompt_API/Using#complete_example) در همین صفحه.

### Requesting input support

این مثال نشان می‌دهد چگونه می‌توان تعیین کرد که آیا ورودی‌های متن و تصویر توسط مدل پشتیبانی می‌شوند.

```js
const status = await LanguageModel.availability({
  expectedInputs: [{ type: "text" }, { type: "image" }],
});
```

### Checking availability for a specific language

این مثال بررسی می‌کند که آیا مدل انگلیسی را پشتیبانی می‌کند، قبل از اینکه از آن بخواهیم متن ژاپنی را به انگلیسی ترجمه کند.

```js
const status = await LanguageModel.availability({
  expectedInputs: [{ type: "text", languages: ["ja"] }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});

if (status === "available") {
  const session = await LanguageModel.create({
    expectedInputs: [{ type: "text", languages: ["ja"] }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });

  const translation = await session.prompt([
    {
      role: "user",
      content: "Translate the following text into English",
    },
    {
      role: "user",
      content: "桜はきれいです",
    },
  ]);

  console.log(translation);
}
```

### Checking availability for multimodal input

[ورودی چندوجهی](/en-US/docs/Web/API/Prompt_API/Multimodal) نشست‌هایی را توصیف می‌کند که می‌توانند از بیش از یک نوع ورودی مانند متن و تصویر استفاده کنند.
از آنجا که در دسترس بودن انواع ورودی بسته به مدل زبانی متفاوت است، کد شما باید قبل از ایجاد نشست، در دسترس بودن حالت‌های موردنظر را بررسی کند.
یک نمونه در اینجا نشان داده شده است.

```js
const availability = await LanguageModel.availability({
  expectedInputs: [{ type: "text" }, { type: "image" }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});

if (availability === "unavailable") {
  console.warn("This configuration is not supported.");
} else {
  const session = await LanguageModel.create({
    expectedInputs: [{ type: "text" }, { type: "image" }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("LanguageModel.create_static", "LanguageModel.create()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [Using the Prompt API](/en-US/docs/Web/API/Prompt_API/Using)