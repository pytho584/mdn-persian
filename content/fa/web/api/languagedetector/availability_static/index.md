---
title: "LanguageDetector: availability() static method"
short-title: availability()
slug: Web/API/LanguageDetector/availability_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.LanguageDetector.availability_static
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

متد ایستای **`availability()`** از رابط {{domxref("LanguageDetector")}} یک مقدار شمارشی برمی‌گرداند که نشان می‌دهد آیا مدل هوش مصنوعی مرورگر از پیکربندی مشخصی از `LanguageDetector` پشتیبانی می‌کند یا نه.

## نحو

```js-nolint
LanguageDetector.availability(options)
```

### پارامترها

- `options`
  - : شیئی که گزینه‌های پیکربندی را برای `LanguageDetector` مشخص می‌کند. مقادیر ممکن شامل موارد زیر هستند:
    - `expectedInputLanguages`
      - : آرایه‌ای از رشته‌ها که زبان‌های مورد انتظار متن ورودی را برای تشخیص زبان مشخص می‌کند. این‌ها باید {{glossary("BCP 47 language tag", "BCP 47 language tags")}} معتبر باشند. پیش‌فرض `["en"]` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار شمارشی تکمیل می‌شود که نشان می‌دهد آیا پشتیبانی برای یک پیکربندی مشخص از `LanguageDetector` موجود است (یا در آینده موجود خواهد بود)، یا اگر نتوان پشتیبانی را تعیین کرد، با `null` تکمیل می‌شود.

مقادیر ممکن عبارت‌اند از:

- `available`
  - : مرورگر از پیکربندی داده‌شده پشتیبانی می‌کند و می‌توان بلافاصله از آن استفاده کرد.
- `downloadable`
  - : مرورگر از پیکربندی داده‌شده پشتیبانی می‌کند، اما ابتدا باید یک مدل هوش مصنوعی، یا برخی داده‌های تنظیم دقیق (fine-tuning) برای مدل دانلود کند.
- `downloading`
  - : مرورگر از پیکربندی داده‌شده پشتیبانی می‌کند، اما باید دانلود در حال انجام را قبل از ادامه به پایان برساند.
- `unavailable`
  - : مرورگر از پیکربندی داده‌شده پشتیبانی نمی‌کند، یا API تشخیص زبان توسط {{httpheader('Permissions-Policy/language-detector','language-detector')}} {{httpheader("Permissions-Policy")}} مسدود شده است.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} صفحه هنوز فعال نباشد، پرتاب می‌شود.
- `OperationError` {{domxref("DOMException")}}
  - : اگر مقداردهی اولیه مدل هوش مصنوعی به هر دلیلی شکست بخورد، پرتاب می‌شود.
- `UnknownError` {{domxref("DOMException")}}
  - : اگر فراخوانی `availability()` به هر دلیل دیگری، یا دلیلی که عامل کاربر (user agent) مایل به افشای آن نبود، ناموفق باشد، پرتاب می‌شود.

## مثال‌ها

### استفاده پایه از `availability()`

در قطعه کد زیر، ابتدا با استفاده از متد `availability()` در دسترس بودن مدل را برای تشخیص چند زبان بررسی می‌کنیم:

- اگر مقدار `unavailable` برگردد، یک پیام خطای مناسب در کنسول چاپ می‌کنیم.
- اگر مقدار `available` برگردد، با استفاده از متد {{domxref("LanguageDetector.create_static", "create()")}} یک تشخیص‌دهنده زبان می‌سازیم و `expectedInputLanguages` را به آن پاس می‌دهیم. مدل هوش مصنوعی مورد نیاز در دسترس است، بنابراین می‌توانیم بلافاصله از آن استفاده کنیم.
- اگر مقدار دیگری برگردد (یعنی `downloadable` یا `downloading`)، همان فراخوانی متد `create()` را اجرا می‌کنیم، اما این بار یک `monitor` نیز اضافه می‌کنیم که درصد دانلود مدل را هر بار که رویداد {{domxref("CreateMonitor/downloadprogress_event", "downloadprogress")}} رخ می‌دهد، ثبت می‌کند.

```js
async function getDetector(languages) {
  const availability = await LanguageDetector.availability({
    expectedInputLanguages: languages,
  });
  if (availability === "unavailable") {
    console.log(`Detection not supported; try a different set of languages.`);
    return undefined;
  } else if (availability === "available") {
    return await LanguageDetector.create({
      expectedInputLanguages: languages,
    });
  }
  return await LanguageDetector.create({
    expectedInputLanguages: languages,
    monitor(monitor) {
      monitor.addEventListener("downloadprogress", (e) => {
        console.log(`Downloaded ${Math.floor(e.loaded * 100)}%`);
      });
    },
  });
}

const detector = await getDetector(["en-US", "zh"]);
```

### تشخیص پشتیبانی از زبان

```js
async function langSupport(language) {
  const availability = await LanguageDetector.availability({
    expectedInputLanguages: [language],
  });
  return availability;
}

await langSupport("en");
await langSupport("pt");
await langSupport("zh");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از APIهای مترجم و تشخیص زبان](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)