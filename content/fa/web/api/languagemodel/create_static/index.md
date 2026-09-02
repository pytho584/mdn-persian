---
title: "LanguageModel: create() static method"
short-title: create()
slug: Web/API/LanguageModel/create_static
page-type: web-api-static-method
browser-compat: api.LanguageModel.create_static
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

متد ایستای **`create()`** از رابط {{domxref("LanguageModel")}} یک نمونه جدید از {{domxref("LanguageModel")}} می‌سازد و در صورت عدم وجود، داده‌های مدل مربوطه را به‌طور خودکار دانلود می‌کند.

## Syntax

```js-nolint
LanguageModel.create()
LanguageModel.create(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء که گزینه‌های ایجاد یک نشست {{domxref("LanguageModel")}} را مشخص می‌کند. ویژگی‌ها عبارتند از:
    - `expectedInputs`
      - : آرایه‌ای از اشیاء که نمایانگر حالت‌ها و زبان‌های ورودی مورد نیاز هستند.
        هر شیء می‌تواند شامل ویژگی‌های زیر باشد:
        - `type`
          - : یک مقدار شمارشی که نوع محتوا را نشان می‌دهد. باید یکی از موارد زیر باشد:
            - `text`
              - : محتوای متنی ساده.
            - `image`
              - : محتوای تصویری.
            - `audio`
              - : محتوای صوتی.
            - `tool-call`
              - : فراخوانی یک ابزار توسط مدل.
            - `tool-response`
              - : نتیجه یک فراخوانی ابزار.
        - `languages` {{optional_inline}}
          - : آرایه‌ای از رشته‌های حاوی برچسب‌های زبان [BCP 47](https://www.rfc-editor.org/rfc/rfc5646) (برای مثال، `en`، `fr`، `ja`) که انتظار می‌رود نشست برای این نوع محتوا از آن‌ها پشتیبانی کند. عامل کاربر (user agent) از این لیست برای تعیین اینکه آیا مدل از زبان‌های مشخص شده پشتیبانی می‌کند و برای انتخاب مؤلفه‌های مناسب مدل یا تنظیمات دقیق (fine-tunings) استفاده می‌کند.
    - `expectedOutputs`
      - : آرایه‌ای از اشیاء که نمایانگر حالت‌ها و زبان‌های خروجی مورد نیاز هستند.
        هر شیء می‌تواند شامل ویژگی‌های زیر باشد:
        - `type`
          - : یک مقدار شمارشی که نوع محتوا را نشان می‌دهد. باید یکی از موارد زیر باشد:
            - `text`
              - : محتوای متنی ساده.
            - `image`
              - : محتوای تصویری.
            - `audio`
              - : محتوای صوتی.
            - `tool-call`
              - : فراخوانی یک ابزار توسط مدل.
            - `tool-response`
              - : نتیجه یک فراخوانی ابزار.
        - `languages` {{optional_inline}}
          - : آرایه‌ای از رشته‌های حاوی برچسب‌های زبان [BCP 47](https://www.rfc-editor.org/rfc/rfc5646) (برای مثال، `en`، `fr`، `ja`) که انتظار می‌رود نشست برای این نوع محتوا از آن‌ها پشتیبانی کند. عامل کاربر از این لیست برای تعیین اینکه آیا مدل از زبان‌های مشخص شده پشتیبانی می‌کند و برای انتخاب مؤلفه‌های مناسب مدل یا تنظیمات دقیق استفاده می‌کند.
    - `initialPrompts`
      - : آرایه‌ای از اشیاء که نمایانگر پیام‌هایی هستند که در زمان ایجاد یک نشست مدل زبانی ارسال می‌شوند. این امکان را به مدل می‌دهد تا دستورالعمل‌ها یا گفتگوی قبلی را بدون نیاز به ارسال مجدد آن‌ها با هر پرسش جدید «به خاطر بسپارد». هر شیء می‌تواند شامل ویژگی‌های زیر باشد:
        - `role`
          - : رشته‌ای که نشان می‌دهد پیام از چه دیدگاهی نوشته شده است. باید یکی از موارد زیر باشد:
            - `system`
              - : یک دستورالعمل در سطح سیستم که رفتار کلی مدل را هدایت می‌کند. این باید اولین دستورالعمل ارسال شده به مدل باشد.
            - `user`
              - : پیامی از طرف کاربر که API باید به آن پاسخ دهد.
            - `assistant`
              - : ورودی که زمینه‌ای را برای دستیار هوش مصنوعی فراهم می‌کند، مانند شخصیت یا قالب پاسخ‌های آن. چنین پیام‌هایی عمدتاً برای ارائه زمینه/تاریخچه و شکل‌دهی بیشتر به نحوه پاسخ‌دهی مدل استفاده می‌شوند.
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
                  - : فراخوانی یک ابزار توسط مدل.
                - `tool-response`
                  - : نتیجه یک فراخوانی ابزار.
            - `value`
              - : محتوای پیام. اگر `type` برابر `text` باشد، این مقدار همیشه یک رشته است. اگر `type` برابر `audio` یا `image` باشد، `value` می‌تواند یکی از چندین نوع شیء مختلف باشد؛ برای اطلاعات بیشتر به [چه انواع داده‌ای پذیرفته می‌شوند؟](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) مراجعه کنید.
        - `prefix` {{optional_inline}}
          - : یک مقدار بولی، به طور پیش‌فرض `false`. وقتی `true` باشد، پیام به عنوان پیشوندی برای پاسخ بعدی مدل در نظر گرفته می‌شود نه یک نوبت کامل.
    - `monitor`
      - : ارجاعی به یک تابع callback از نوع {{domxref("CreateMonitor")}} برای دریافت رویدادهای پیشرفت دانلود.
    - `signal`
      - : یک {{domxref("AbortSignal")}} برای لغو ایجاد نشست.
    - `tools`
      - : آرایه‌ای از اشیاء که نمایانگر ابزارهای در دسترس هوش مصنوعی هستند.
        هر شیء می‌تواند شامل ویژگی‌های زیر باشد:
        - `name`
          - : رشته‌ای که به ابزار یک نام یکتا می‌دهد که مدل هنگام فراخوانی ابزار از آن استفاده می‌کند.
        - `description`
          - : رشته‌ای که کار ابزار را توصیف می‌کند. مدل از این توضیحات برای تصمیم‌گیری در مورد اینکه آیا و چه زمانی ابزار را فراخوانی کند استفاده می‌کند.
        - `inputSchema`
          - : یک [JSON Schema](https://json-schema.org/) که پارامترهای ورودی ابزار را توصیف می‌کند. مدل از این طرحواره برای ساخت آرگومان‌هایی که به تابع `execute` ابزار ارسال می‌کند استفاده می‌کند.
        - `execute`
          - : یک تابع callback که عامل کاربر وقتی مدل این ابزار را فراخوانی می‌کند، آن را اجرا می‌کند. آرگومان‌های آن به مدل مورد استفاده بستگی دارد. باید یک {{jsxref("Promise")}} برگرداند که با یک {{jsxref("String")}} نمایانگر نتیجه ابزار حل شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک نمونه جدید از {{domxref("LanguageModel")}} حل می‌شود.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر عملیات از طریق گزینه `signal` لغو شده باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند فراخواننده کاملاً فعال (fully active) نباشد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر استفاده از متد توسط یک {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} مسدود شده باشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر یکی از موارد زیر رخ دهد، پرتاب می‌شود:
    - `role` یک پیام `assistant` باشد و `type` آن چیزی غیر از `text` باشد.
    - `type` یک پیام `text` باشد و `value` آن یک رشته نباشد.
    - متن ورودی یا خروجی به زبانی باشد که عامل کاربر برای درخواست‌نویسی (prompting) از آن پشتیبانی نمی‌کند.
    - `type` یک پیام `image` یا `audio` باشد اما این نوع در `expectedInputs` فهرست نشده باشد، یا `value` یک [نوع داده پذیرفته شده](/en-US/docs/Web/API/Prompt_API/Multimodal#what_data_types_are_accepted) نباشد.
- `OperationError` {{domxref("DOMException")}}
  - : اگر ایجاد به هر دلیل دیگری غیر از موارد ذکر شده در سایر انواع استثنا شکست بخورد، پرتاب می‌شود.
- `QuotaExceededError` {{domxref("DOMException")}}
  - : اگر محتوای ارائه شده در `initialPrompts` از {{domxref("LanguageModel.contextWindow")}} مدل تجاوز کند، پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر یکی از موارد زیر رخ دهد، پرتاب می‌شود:
    - هیچ پیامی در آرایه پیام‌ها وجود نداشته باشد.
    - ویژگی `prefix` یک پیام روی `true` تنظیم شده باشد و:
      - `role` پیام `assistant` نباشد.
      - پیام آخرین آیتم در آرایه پیام‌ها نباشد.
- `TypeError` {{domxref("DOMException")}}
  - : اگر یکی از موارد زیر رخ دهد، پرتاب می‌شود:
    - `role` یک پیام `system` باشد اما اولین پیام ارسال شده به زمینه نباشد.

## توضیحات

متد `create()` یک نشست جدید از مدل زبانی می‌سازد و در صورت عدم وجود، مدل را به‌طور خودکار دانلود می‌کند.
شما می‌توانید پیشرفت دانلود یک مدل را با استفاده از گزینه [`monitor`](#monitor) پیگیری کنید.

قبل از فراخوانی `create()`، از {{domxref("LanguageModel.availability_static", "LanguageModel.availability()")}} استفاده کنید تا بررسی کنید آیا پیکربندی مورد نظر پشتیبانی می‌شود.

پس از ایجاد یک نشست، از متدهای نمونه آن — {{domxref("LanguageModel.prompt()")}}، {{domxref("LanguageModel.promptStreaming()")}}، {{domxref("LanguageModel.append()")}} و موارد دیگر — برای تعامل با مدل استفاده کنید.

## امنیت

[فعال‌سازی موقت کاربر](/en-US/docs/Web/Security/Defenses/User_activation) (Transient user activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند.

## مثال‌ها

### ایجاد یک نشست پایه

این مثال یک نشست پیش‌فرض ایجاد می‌کند و سپس از آن نتیجه جمع `2` و `2` را می‌پرسد.
توجه داشته باشید که متن به طور پیش‌فرض پشتیبانی می‌شود، بنابراین مدل دانلود شده باید برای این مورد مناسب باشد.

```js
const session = await LanguageModel.create();
const answer = await session.prompt("What is 2 + 2?");
console.log(answer);
```

همچنین به [استفاده از Prompt API > ایجاد یک نشست `LanguageModel`](/en-US/docs/Web/API/Prompt_API/Using#creating_a_languagemodel_session) مراجعه کنید.

### ایجاد یک نشست با یک درخواست سیستمی

مثال زیر به هوش مصنوعی دستورالعمل‌هایی در مورد شخصیتی که باید قبل از تولید پاسخ اتخاذ کند، ارائه می‌دهد.

```js
const session = await LanguageModel.create({
  initialPrompts: [
    {
      role: "system",
      content: "You are a concise assistant. Respond in one sentence.",
    },
  ],
});

const response = await session.prompt("What is photosynthesis?");
console.log(response);
```

همچنین به [افزودن زمینه با ورودی‌های اولیه و جاری > ارائه درخواست‌های اولیه هنگام ایجاد نشست](/en-US/docs/Web/API/Prompt_API/Adding_context#providing_initial_prompts_during_session_creation) مراجعه کنید.

### نظارت بر پیشرفت دانلود

این کد نشان می‌دهد که چگونه می‌توانید پیشرفت دانلود یک مدل را نظارت کنید.
توجه داشته باشید که اگر مدل در دسترس نباشد یا از قبل موجود باشد، این رویداد هرگز فعال نخواهد شد.

```js
const session = await LanguageModel.create({
  monitor(monitor) {
    monitor.addEventListener("downloadprogress", ({ loaded, total }) => {
      console.log(`Model download: ${Math.round((loaded / total) * 100)}%`);
    });
  },
});
```

همچنین به [استفاده از Prompt API > نظارت بر پیشرفت دانلود](/en-US/docs/Web/API/Prompt_API/Using#monitoring_download_progress) مراجعه کنید.

### ارائه درخواست‌های چند-نمونه (few-shot)

مثال زیر نشان می‌دهد که چگونه از یک [درخواست چند-نمونه](/en-US/docs/Web/API/Prompt_API/Adding_context#few-shot_prompts) برای درخواست یک کار خاص (ترجمه به فرانسوی) که باید در قالبی خاص تحویل داده شود، استفاده کنید، قبل از ارائه چند مثال برای کمک به یادگیری قالب خروجی صحیح.

```js
const session = await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en", "fr"] }],
  initialPrompts: [
    {
      role: "system",
      content:
        "Translate the user's input to French. Use the output format 'English input: French output'",
    },
    { role: "user", content: "Hello" },
    { role: "assistant", content: "Hello: Bonjour" },
    { role: "user", content: "Goodbye" },
    { role: "assistant", content: "Goodbye: Au revoir" },
    { role: "user", content: "The train is late" },
    {
      role: "assistant",
      content: "The train is late: Le train est en retard",
    },
    { role: "user", content: "My shoes are pink" },
    {
      role: "assistant",
      content: "My shoes are pink: Mes chaussures sont roses",
    },
  ],
});

const result = await session.prompt("Window");
console.log(result); // "Window: Fenêtre"
```

همچنین به [افزودن زمینه با ورودی‌های اولیه و جاری > درخواست‌های چند-نمونه](/en-US/docs/Web/API/Prompt_API/Adding_context#few-shot_prompts) مراجعه کنید.

### تعریف یک ابزار با یک تابع callback

این مثال یک نشست با یک ابزار فرضی «دریافت آب و هوا» ایجاد می‌کند. وقتی مدل تصمیم می‌گیرد ابزار را فراخوانی کند، عامل کاربر `execute()` را با آرگومان‌های ارائه شده توسط مدل فراخوانی می‌کند.

```js
async function getWeatherData(location) {
  const response = await fetch(
    `https://api.example.com/weather?city=${location}`,
  );
  const data = await response.json();
  return `${data.temp}°C, ${data.description}`;
}

const session = await LanguageModel.create({
  tools: [
    {
      name: "getWeather",
      description: "Returns the current weather for a given city.",
      inputSchema: {
        type: "object",
        properties: {
          location: { type: "string", description: "The city name." },
        },
        required: ["location"],
      },
      execute: async (...args) => {
        const location = args[0];
        return await getWeatherData(location);
      },
    },
  ],
});

const response = await session.prompt("What's the weather like in Tokyo?");
console.log(response);
```

### لغو یک نشست

مثال زیر به کاربر امکان لغو یک درخواست را می‌دهد. این کار را ابتدا با ایجاد یک {{domxref("AbortController")}} و اختصاص متد `abort()` آن به یک کنترل‌کننده کلیک دکمه لغو انجام می‌دهد. سپس `create()` را فراخوانی کرده و `AbortController.signal` را به عنوان ویژگی `signal` ارسال می‌کند.

```js
const controller = new AbortController();

const cancelButton = document.getElementById("cancel-button");
cancelButton.addEventListener("click", () => controller.abort());

const session = await LanguageModel.create({
  signal: controller.signal,
  initialPrompts: [
    {
      role: "system",
      content: "You are a helpful assistant.",
    },
  ],
});
```

همچنین به [استفاده از Prompt API > لغو عملیات و نابودسازی نمونه‌ها](/en-US/docs/Web/API/Prompt_API/Using#cancelling_operations_and_destroying_instances) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LanguageModel.availability_static", "LanguageModel.availability()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)
- [افزودن زمینه با ورودی‌های اولیه و جاری](/en-US/docs/Web/API/Prompt_API/Adding_context)