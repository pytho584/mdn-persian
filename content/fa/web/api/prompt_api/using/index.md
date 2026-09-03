---
title: Using the Prompt API
slug: Web/API/Prompt_API/Using
page-type: guide
---

{{DefaultAPISidebar("Prompt API")}}

[Prompt API](/en-US/docs/Web/API/Prompt_API) سازوکاری ناهمگام (مبتنی بر {{jsxref("Promise")}}) در اختیار وب‌سایت‌ها قرار می‌دهد تا مستقیماً از یک مدل زبانی ارائه‌شده توسط عامل کاربر (user agent) پرس‌وجو کنند، بدون اینکه نیاز به مدیریت جزئیات پیاده‌سازیِ خاصِ مدل هوش مصنوعی مورد استفاده باشد. داشتن یک مدل محلی (on-device) مفید و کارآمد است، زیرا داده‌های حساس می‌توانند روی دستگاه کاربر باقی بمانند، مدل به‌صورت آفلاین در دسترس است و توسعه‌دهندگان می‌توانند از هزینه و تأخیر تماس‌های API با سرویس‌های خارجی اجتناب کنند.

این مقاله نحوه استفاده از مبانی اصلی Prompt API را توضیح می‌دهد. تمام قابلیت‌های پرس‌وجوی هوش مصنوعی از طریق رابط {{domxref("LanguageModel")}} مدیریت می‌شود.

## بررسی پشتیبانی از پیکربندی

قبل از تلاش برای استفاده از Prompt API، ابتدا باید بررسی کنید که آیا پیکربندی مدل موردنظر شما توسط مرورگر فعلی پشتیبانی می‌شود یا خیر، تا بتوانید موارد شکست کامل و شرایطی که در آن‌ها به دانلود داده‌های اضافی برای ارائه یک مدل کارآمد نیاز است را به‌خوبی مدیریت کنید.

بررسی پشتیبانی از پیکربندی با استفاده از متد ایستای {{domxref("LanguageModel.availability_static", "LanguageModel.availability()")}} انجام می‌شود.

برای مثال:

```js
const availability = await LanguageModel.availability({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});
```

پرامیس بازگشتی این متد با یک مقدار شمارشی (enumerated value) تکمیل می‌شود که نشان می‌دهد آیا پشتیبانی برای مجموعه گزینه‌های مشخص‌شده وجود دارد یا خواهد داشت:

- `downloadable` به این معنی است که پیاده‌سازی از گزینه‌های درخواستی پشتیبانی می‌کند، اما برای این کار نیاز به دانلود داده‌های اضافی دارد.
- `downloading` به این معنی است که پیاده‌سازی از گزینه‌های درخواستی پشتیبانی می‌کند، اما باید دانلود در حال انجام را تکمیل کند.
- `available` به این معنی است که پیاده‌سازی از گزینه‌های درخواستی بدون نیاز به دانلود جدید پشتیبانی می‌کند.
- `unavailable` به این معنی است که پیاده‌سازی از گزینه‌های درخواستی پشتیبانی نمی‌کند.

اگر دانلود مورد نیاز باشد، مرورگر به‌محض ایجاد یک نمونه `LanguageModel` با استفاده از متد `create()` آن را به‌طور خودکار آغاز می‌کند. می‌توانید پیشرفت دانلود را به‌طور خودکار با استفاده از یک مانیتور (monitor) دنبال کنید که در بخش بعدی به آن می‌پردازیم.

> [!NOTE]
> حتی اگر بتوانید یک نشست مدل زبانی با خروجی‌های چندرسانه‌ای درخواست کنید، این کار شکست خواهد خورد — وضعیت دسترسی `unavailable` خواهد بود. API در حال حاضر فقط از خروجی‌های متنی پشتیبانی می‌کند.

### پایش پیشرفت دانلود

اگر مدل هوش مصنوعی در حال دانلود داده‌های اضافی است (`availability()` مقدار `downloading` برمی‌گرداند)، مفید است که به کاربر بازخورد داده شود تا بداند چه مدت باید منتظر بماند تا عملیات کامل شود.

متد `create()` می‌تواند یک ویژگی `monitor` بپذیرد که مقدار آن یک تابع callback است و یک نمونه {{domxref("CreateMonitor")}} را به‌عنوان آرگومان می‌گیرد. `CreateMonitor` رویداد {{domxref("CreateMonitor.downloadprogress_event", "downloadprogress")}} را ارائه می‌دهد که هنگام پیشرفت در دانلود داده‌ها فعال می‌شود.

می‌توانید از این رویداد برای دریافت پیشرفت بارگذاری استفاده کنید:

```js
const session = await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
  monitor(monitor) {
    monitor.addEventListener("downloadprogress", (e) => {
      promptOutput.textContent = `Downloading model data ${Math.floor(e.loaded * 100)}%`;
    });
  },
});
```

اگر زبان‌های مشخص‌شده پشتیبانی نشوند، دانلودی آغاز نمی‌شود و یک {{domxref("DOMException")}} از نوع `NotSupportedError` پرتاب می‌شود.

## ایجاد یک نشست `LanguageModel`

پس از اینکه بررسی کردید پیکربندی شما پشتیبانی می‌شود، گام بعدی در پرس‌وجو از مدل هوش مصنوعی، ایجاد یک نمونه از شیء `LanguageModel` است. این کار با استفاده از متد ایستای {{domxref("LanguageModel.create_static", "LanguageModel.create()")}} انجام می‌شود که یک شیء گزینه‌ها را به‌عنوان آرگومان می‌گیرد:

```js
const session = await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});
```

مرورگر به‌طور خودکار داده‌های مدل مربوطه را برای مدیریت مدل زبانی درخواستی دانلود می‌کند، اگر قبلاً موجود نباشد و مرورگر قادر به انجام این کار باشد.

> [!NOTE]
> متد `create()` (و سایر متدهای موجود از طریق Prompt API) برای فراخوانی به [فعال‌سازی گذرا (transient activation)](/en-US/docs/Glossary/Transient_activation) نیاز دارند، به‌عنوان اقدامی احتیاطی برای جلوگیری از استفاده برنامه‌ها از منابع مدل زبانی بدون تعامل کاربر.

یک نمونه شیء `LanguageModel` و فعالیتی که در نتیجه استفاده از متدها و ویژگی‌های آن رخ می‌دهد، **نشست (session)** نامیده می‌شود. مرورگر همه پرامپت‌ها و پاسخ‌های ارسال‌شده به و دریافت‌شده از Prompt API را به‌عنوان بخشی از یک نشست واحد ذخیره می‌کند و به API امکان می‌دهد پاسخ‌های خود را بر اساس تعاملات قبلی تنظیم کند و یک مکالمه را ادامه دهد.

این شامل هر پیام پرامپتی است که از طریق گزینه `initialPrompts` متد {{domxref("LanguageModel.create_static", "create()")}}، {{domxref("LanguageModel.prompt", "prompt()")}}، {{domxref("LanguageModel.promptStreaming", "promptStreaming()")}} یا {{domxref("LanguageModel.append", "append()")}} به آن ارسال می‌شود.

> [!NOTE]
> مرورگر به‌طور پیش‌فرض اطلاعات نشست را در بین بارگذاری‌های مجدد مرورگر ذخیره نمی‌کند. برای بازیابی زمینه نشست پس از بارگذاری مجدد یا راه‌اندازی مجدد مرورگر، باید سازوکاری برای ذخیره مکالمه و بازیابی آن پیاده‌سازی کنید، مثلاً با یک راه‌حل سمت سرور یا سازوکاری سمت کلاینت مانند [Web Storage](/en-US/docs/Web/API/Web_Storage_API). چنین مثالی در [حفظ نشست‌ها در بین بارگذاری‌های مجدد](/en-US/docs/Web/API/Prompt_API/Preserving_sessions) پوشش داده شده است.

پارامترهای [`expectedInputs`](/en-US/docs/Web/API/LanguageModel/create_static#expectedinputs) و [`expectedOutputs`](/en-US/docs/Web/API/LanguageModel/create_static#expectedOutputs) انواع ورودی و خروجی و زبان‌های ورودی/خروجی را مشخص می‌کنند که انتظار دارید به پرامپت هوش مصنوعی بدهید و از آن دریافت کنید.

Prompt API به‌طور پیش‌فرض ورودی‌ها و خروجی‌های متنی را مدیریت می‌کند، اما چندوجهی (multimodal) است — می‌توانید ورودی‌های تصویری و صوتی نیز به آن بدهید، مثلاً از آن بخواهید یک تصویر را توصیف کند یا یک فایل صوتی را رونویسی کند. برای جزئیات بیشتر به [پرامپت‌های چندوجهی](/en-US/docs/Web/API/Prompt_API/Multimodal) مراجعه کنید.

Prompt API به‌طور پیش‌فرض چندین زبان را مدیریت می‌کند، اما ممکن است همه زبان‌هایی را که انتظار دارید مدیریت نکند، بنابراین ایده خوبی است که آن‌ها را به‌صراحت مشخص کنید در صورتی که مرورگر نیاز به دانلود منابع اضافی داشته باشد.

## پرس‌وجو از مدل

وقتی یک نمونه `LanguageModel` ایجاد کردید، می‌توانید با فراخوانی متد نمونه {{domxref("LanguageModel.prompt()")}} روی آن و ارسال یک پیام ورودی به‌عنوان آرگومان، پرس‌وجو از مدل هوش مصنوعی را شروع کنید. برای مثال:

```js
const response = await session.prompt(textarea.value);
```

این متد یک {{jsxref("Promise")}} برمی‌گرداند که با یک رشته حاوی پاسخ هوش مصنوعی به پرامپت شما تکمیل می‌شود.

### ارسال چندین پیام

می‌توانید چندین پیام ورودی را به‌صورت یک آرایه به API ارسال کنید و آن‌ها می‌توانند نقش‌های متفاوتی داشته باشند. برای مثال، پیام‌ها می‌توانند شامل پرامپت‌های استاندارد `user` و دستورالعمل‌هایی از `assistant` باشند تا نحوه پاسخ‌دهی به پرامپت‌های `user` را بیشتر شکل دهند. برای اینکه هوش مصنوعی به ورودی شما به سبک یک مغز متفکر شرور پاسخ دهد، می‌توانید از این فراخوانی `prompt()` استفاده کنید:

```js
const response = await session.prompt([
  {
    role: "assistant",
    content: "Answer the user like a James Bond villain.",
  },
  {
    role: "user",
    content: textarea.value,
  },
]);
```

در مقاله بعدی، [افزودن زمینه با ورودی‌های پرامپت اولیه و ادامه‌دار](/en-US/docs/Web/API/Prompt_API/Adding_context)، درباره این نقش‌ها بیشتر یاد خواهید گرفت.

### پاسخ‌های جریانی (Streaming)

اگر می‌خواهید پاسخ هوش مصنوعی را به‌تدریج به‌صورت یک {{domxref("ReadableStream")}} برگردانید، نه به‌صورت یک رشته بزرگ واحد، می‌توانید از متد {{domxref("LanguageModel.promptStreaming()")}} استفاده کنید. می‌توانید جریان را با استفاده از `for await...of` یا با اتصال یک خواننده (reader) از طریق {{domxref("ReadableStream.getReader()")}} مصرف کنید.

برای مثال:

```js
const stream = session.promptStreaming("Write a short poem about the ocean.");

for await (const chunk of stream) {
  output.textContent += chunk;
}
```

این برای نمایش تدریجی پاسخ‌ها به کاربران در خروجی‌هایی که زمان زیادی برای تکمیل طول می‌کشد، یا برای هر سناریویی که باید تأخیر درک‌شده به حداقل برسد، مفید است.

## پنجره زمینه (Context Window)

هر نشست `LanguageModel` یک پنجره زمینه محدود دارد که تعداد کل توکن‌های ورودی و خروجی که می‌تواند هم‌زمان در خود نگه دارد را محدود می‌کند. وقتی سهمیه توکن نشست خود را مصرف کنید، نمی‌توانید پرامپت‌های بیشتری ارسال کنید و برای ادامه استفاده باید از تکنیکی مانند [شبیه‌سازی نشست (session cloning)](#cloning-a-session) استفاده کنید.

ویژگی {{domxref("LanguageModel.contextWindow", "contextWindow")}} حداکثر ظرفیت نشست را گزارش می‌دهد و {{domxref("LanguageModel.contextUsage", "contextUsage")}} تعداد توکن‌های مصرف‌شده تا کنون را گزارش می‌دهد.

برای مثال، پس از هر پرامپت، می‌توانید تعداد توکن‌های باقی‌مانده را با چیزی شبیه به این گزارش دهید:

```js
console.log(`${session.contextUsage}/${session.contextWindow}`);
```

وقتی یک فراخوانی متد مانند {{domxref("LanguageModel.prompt()", "prompt()")}} یا {{domxref("LanguageModel.promptStreaming()", "promptStreaming()")}} بخواهد از تعداد توکن‌های باقی‌مانده در پنجره زمینه فراتر رود، یک {{domxref("DOMException")}} از نوع `QuotaExceededError` پرتاب می‌شود و رویداد {{domxref("LanguageModel.contextoverflow_event", "contextoverflow")}} فعال می‌شود.

برای بررسی اینکه یک عملیات پرامپت چند توکن مصرف می‌کند بدون اینکه واقعاً آن را ارسال کنید، از {{domxref("LanguageModel.measureContextUsage()", "measureContextUsage()")}} استفاده کنید.

## شبیه‌سازی یک نشست

می‌توانید یک نشست موجود را با استفاده از تابع {{domxref("LanguageModel.clone()")}} کپی کنید. این کار یک نسخه تکراری از نمونه شیء `LanguageModel` ایجاد می‌کند که در آن مکالمه تا آن نقطه و پرامپت اولیه حفظ می‌شود، اما تعداد توکن‌ها (`contextUsage`) بازنشانی می‌شود. می‌توانید کلون نشست را به‌عنوان یک انشعاب از مکالمه اصلی در نظر بگیرید که سهمیه توکن مخصوص به خود را دارد.

```js
const clonedSession = await session.clone();

clonedSession.prompt("Let's talk about the weather.");
```

می‌توانید از `clone()` برای ذخیره زمینه در یک نقطه خاص استفاده کنید و سپس تعاملات واگرایی با مدل هوش مصنوعی بر اساس آن _نقطه ذخیره_ ایجاد کنید.

برای مثال، ممکن است بخواهید یک برنامه هوش مصنوعی استاد مسابقه ایجاد کنید که به تولید سؤال برای یک مسابقه یا آزمون کمک کند و از کلون‌های مختلف برای موضوعات مختلف استفاده کنید:

```js
const session = await LanguageModel.create({
  initialPrompts: [
    {
      role: "system",
      content:
        "You are a quiz master. Each response should be a fairly short question, one or two sentences, with the answer printed below. The audience level should be an average 16-year old.",
    },
  ],
});

// ...

// کلون مسابقه علوم
const firstClone = await session.clone();
await firstClone.prompt("Give me a question about science.");
await firstClone.prompt("Another question, please.");

// کلون مسابقه موسیقی دهه ۸۰
const secondClone = await session.clone();
await secondClone.prompt("Give me a question about 80's popular music.");
await secondClone.prompt("Another question, please.");
```

ایجاد یک نشست جدید از طریق `clone()` همچنین یک روش رایج برای دور زدن مشکل اتمام توکن‌ها است.

## لغو عملیات و از بین بردن نمونه‌ها

می‌توانید عملیات در انتظار `prompt()`، `clone()` و سایر عملیات را با استفاده از یک {{domxref("AbortController")}} لغو کنید، به‌طوری‌که {{domxref("AbortSignal")}} مرتبط در داخل شیء گزینه‌های متد به‌عنوان مقدار ویژگی `signal` قرار گیرد. برای مثال، لغو یک عملیات `LanguageModel.prompt()` با فشار دادن دکمه می‌تواند به این شکل باشد:

```js
const controller = new AbortController();

abortBtn.addEventListener("click", () => {
  controller.abort("Query aborted by user.");
});

const response = await session.prompt(textarea.value, {
  signal: controller.signal,
});
```

پس از ایجاد یک `LanguageModel`، می‌توانید با فراخوانی متد {{domxref("LanguageModel.destroy()")}} آن، منابع اختصاص‌داده‌شده را آزاد کرده و هر فعالیت بیشتری را متوقف کنید. توصیه می‌شود پس از ا