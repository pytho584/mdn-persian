---
title: "LanguageDetector: inputQuota property"
short-title: inputQuota
slug: Web/API/LanguageDetector/inputQuota
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LanguageDetector.inputQuota
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

خاصیتِ فقط‌خواندنی **`inputQuota`** در رابط {{domxref("LanguageDetector")}} سهمیهٔ ورودیِ در دسترس مرورگر برای تشخیص زبان را برمی‌گرداند.

## مقدار

عددی که سهمیهٔ ورودی موجود را مشخص می‌کند.

این عدد به پیاده‌سازی وابسته است. برای مثال، اگر محدودیتی فراتر از حافظهٔ کاربر و حداکثر طول رشته‌های جاوااسکریپت وجود نداشته باشد، ممکن است {{jsxref("Infinity")}} باشد، یا در مورد مدل‌های هوش مصنوعی که از طرح توکن/اعتبار استفاده می‌کنند، ممکن است تعداد توکن‌ها باشد.

تنها تضمین این است که اگر سهمیهٔ کافی برای تشخیص زبان متن وجود داشته باشد، `inputQuota` - {{domxref("LanguageDetector.measureInputUsage", "measureInputUsage()")}} غیرمنفی خواهد بود.

## مثال‌ها

### بررسی اینکه آیا سهمیهٔ کافی دارید

در قطعه‌کد زیر، یک نمونهٔ جدید `LanguageDetector` با استفاده از {{domxref("LanguageDetector.create_static", "create()")}} می‌سازیم، سپس سهمیهٔ کل ورودی را از طریق `inputQuota` و میزان مصرف سهمیهٔ ورودی برای تشخیص زبان یک رشتهٔ متنی خاص را از طریق {{domxref("LanguageDetector.measureInputUsage", "measureInputUsage()")}} برمی‌گردانیم.

سپس بررسی می‌کنیم که آیا مصرف ورودیِ آن رشته از کل سهمیهٔ موجود بیشتر است یا نه. اگر بیشتر بود، خطای مناسبی پرتاب می‌کنیم؛ در غیر این صورت، تشخیص زبان رشته را با استفاده از {{domxref("LanguageDetector.detect", "detect()")}} آغاز می‌کنیم.

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

- [استفاده از APIهای Translator و Language Detector](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)