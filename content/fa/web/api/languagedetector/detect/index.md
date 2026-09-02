---
title: "LanguageDetector: detect() method"
short-title: detect()
slug: Web/API/LanguageDetector/detect
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LanguageDetector.detect
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`detect()`** در رابط {{domxref("LanguageDetector")}} زبان یا زبان‌هایی را که یک رشته‌ی متنی به احتمال زیاد در آن‌ها نوشته شده است، با نزدیک‌ترین تطابق شناسایی می‌کند.

## نحو (Syntax)

```js-nolint
detect(input)
detect(input, options)
```

### پارامترها

- `input`
  - : رشته‌ای که متنی را که باید زبانش شناسایی شود، نشان می‌دهد.
- `options` {{optional_inline}}
  - : شیئی که گزینه‌های پیکربندی عملیات `detect()` را مشخص می‌کند. مقادیر احتمالی عبارت‌اند از:
    - `signal`
      - : یک نمونه از شیء {{domxref("AbortSignal")}} که اجازه می‌دهد عملیات `detect()` از طریق {{domxref("AbortController")}} مرتبط لغو شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از اشیاء نشان‌دهنده‌ی زبان‌های شناسایی‌شده تکمیل می‌شود. هر شیء شامل ویژگی‌های زیر است:

- `detectedLanguage`
  - : یک {{glossary("BCP 47 language tag")}} که زبان شناسایی‌شده را نشان می‌دهد.
- `confidence`
  - : عددی بین `0` و `1` که میزان اطمینان مدل هوش مصنوعی را نسبت به درست‌بودن زبان شناسایی‌شده نشان می‌دهد.

مجموع همه‌ی مقادیر `confidence` بازگشتی به لحاظ نظری باید `1` باشد؛ اما ممکن است کمتر باشد، زیرا مقادیر اطمینان بسیار پایین از نتایج حذف می‌شوند.

آخرین عنصر آرایه‌ی بازگشتی همیشه مقدار `detectedLanguage` آن برابر با `und` خواهد بود — این مخفف «undetermined» (نامشخص) است و بیانگر احتمال این است که متن به زبانی نوشته شده باشد که مدل آن را نمی‌شناسد.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر `LanguageDetector` قبلاً از بین رفته باشد (یعنی {{domxref("LanguageDetector.destroy()")}} روی آن فراخوانی شده باشد) یا پس از ایجاد، از طریق [`signal`](/en-US/docs/Web/API/LanguageDetector/create_static#signal) لغو شده باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} جاری فعال نباشد، پرتاب می‌شود.
- {{domxref("QuotaExceededError")}}
  - : اگر عملیات شناسایی زبان از {{domxref("LanguageDetector.inputQuota", "inputQuota")}} موجود فراتر رود، پرتاب می‌شود.

## مثال‌ها

### استفاده‌ی پایه از `detect()`

```js
const detector = await LanguageDetector.create({
  expectedInputLanguages: ["en-US", "zh"],
});

const results = await detector.detect(myTextString);

results.forEach((result) => {
  console.log(`${result.detectedLanguage}: ${result.confidence}`);
});

// Results in logs like this:
// la: 0.8359838724136353
// es: 0.017705978825688362
// sv: 0.012977192178368568
// en: 0.011148443445563316
// und: 0.0003214875760022551
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از APIهای Translator و Language Detector](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)