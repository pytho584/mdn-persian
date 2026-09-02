---
title: "LanguageDetector: destroy() method"
---

---
title: "LanguageDetector: destroy() method"
short-title: destroy()
slug: Web/API/LanguageDetector/destroy
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LanguageDetector.destroy
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`destroy()`** از رابط {{domxref("LanguageDetector")}} منابع تخصیص‌داده‌شده به نمونه‌ی `LanguageDetector` را که روی آن فراخوانی می‌شود آزاد می‌کند و هر فعالیت بیشتر روی آن را متوقف می‌نماید. این یعنی هر فراخوانی متد در حال انجام یا بعدی روی `LanguageDetector` با یک `AbortError` رد می‌شود.

زمانی که دیگر از اشیاء `LanguageDetector` استفاده نمی‌شود، منطقی است که آن‌ها را نابود کنید، زیرا منابع قابل توجهی را در پردازش خود درگیر می‌کنند.

## نحو

```js-nolint
destroy()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثالها

### کاربرد پایه‌ی `destroy()`

```js
const detector = await LanguageDetector.create({
  expectedInputLanguages: ["en-US", "zh"],
});

// ...

detector.destroy();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از APIهای Translator و Language Detector](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)