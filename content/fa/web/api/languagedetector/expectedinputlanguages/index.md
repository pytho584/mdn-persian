---
title: "LanguageDetector: expectedInputLanguages property"
short-title: expectedInputLanguages
slug: Web/API/LanguageDetector/expectedInputLanguages
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LanguageDetector.expectedInputLanguages
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`expectedInputLanguages`** از رابط {{domxref("LanguageDetector")}} زبان‌های مورد انتظار برای تشخیص در متن ورودی را برمی‌گرداند. مشخص کردن زبان‌های ورودی مورد انتظار به بهبود دقت تشخیص زبان کمک می‌کند.

مقدار `expectedInputLanguages` یک نمونه `LanguageDetector` هنگام ایجاد آن از طریق فراخوانی {{domxref("LanguageDetector.create_static", "create()")}} تنظیم می‌شود.

## مقدار

آرایه‌ای از رشته‌ها که زبان‌های ورودی مورد انتظار را مشخص می‌کند. این زبان‌ها {{glossary("BCP 47 language tag", "BCP 47 language tags")}} معتبر خواهند بود.

## مثال‌ها

```js
const detector = await LanguageDetector.create({
  expectedInputLanguages: ["en-US", "zh"],
});

// Logs ["en-US", "zh"]
console.log(detector.expectedInputLanguages);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Translator and Language Detector APIs](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)
