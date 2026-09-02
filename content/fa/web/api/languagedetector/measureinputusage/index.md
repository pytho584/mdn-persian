---
title: "LanguageDetector: measureInputUsage() method"
short-title: measureInputUsage()
slug: Web/API/LanguageDetector/measureInputUsage
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LanguageDetector.measureInputUsage
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`measureInputUsage()`** از رابط {{domxref("LanguageDetector")}} گزارش می‌دهد که برای یک عملیات تشخیص زبان روی یک متن ورودی معین، چه مقدار از سهمیه ورودی مصرف خواهد شد.

## سینتکس

```js-nolint
measureInputUsage(input)
measureInputUsage(input, options)
```

### پارامترها

- `input`
  - : رشته‌ای که متن ورودی موردنظر برای اندازه‌گیری مصرف ورودی را نشان می‌دهد.
- `options` {{optional_inline}}
  - : شیءای که گزینه‌های پیکربندی عملیات `measureInputUsage()` را مشخص می‌کند. مقادیر احتمالی عبارتند از:
    - `signal`
      - : یک نمونه از شیء {{domxref("AbortSignal")}} که امکان لغو عملیات `measureInputUsage()` را از طریق {{domxref("AbortController")}} مرتبط فراهم می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با عددی تحقق می‌یابد که مصرف {{domxref("LanguageDetector.inputQuota", "inputQuota")}} متن ورودی داده‌شده را مشخص می‌کند.

این عدد به پیاده‌سازی وابسته است؛ اگر کمتر از {{domxref("LanguageDetector.inputQuota", "inputQuota")}} باشد، زبان رشته قابل تشخیص است.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که استفاده از API `LanguageDetector` توسط یک {{httpheader('Permissions-Policy/language-detector','language-detector')}} {{httpheader("Permissions-Policy")}} مسدود شده باشد.
- `UnknownError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که فراخوانی `measureInputUsage()` به هر دلیل دیگری شکست بخورد، یا به دلیلی که عامل کاربر مایل به افشای آن نبود.

## مثال‌ها

### بررسی اینکه آیا سهمیه کافی دارید

در قطعه کد زیر، یک نمونه جدید `LanguageDetector` با استفاده از {{domxref("LanguageDetector.create_static", "create()")}} می‌سازیم، سپس سهمیه کل ورودی را از طریق {{domxref("LanguageDetector.inputQuota", "inputQuota")}} و مصرف سهمیه ورودی برای تشخیص زبان یک رشته متنی خاص را از طریق `measureInputUsage()` برمی‌گردانیم.

سپس بررسی می‌کنیم که آیا مصرف ورودی تکی برای آن رشته بیشتر از سهمیه کل موجود است یا خیر. اگر چنین بود، خطای مناسبی پرتاب می‌کنیم؛ در غیر این صورت، تشخیص زبان رشته را با استفاده از {{domxref("LanguageDetector.detect", "detect()")}} آغاز می‌کنیم.

```js
const detector = await LanguageDetector.create({
  expectedInputLanguages: ["en-US", "zh"],
});

const totalInputQuota = detector.inputQuota;
const inputUsage = await detector.measureInputUsage(myTextString);

if (inputUsage > totalInputQuota) {
  throw new Error("Insufficient quota to detect languages.");
} else {
  console.log("Quota available to detect languages.");
  const results = await detector.detect(myTextString);
  // ...
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Translator and Language Detector APIs](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)