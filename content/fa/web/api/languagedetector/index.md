```
---
title: LanguageDetector
slug: Web/API/LanguageDetector
page-type: web-api-interface
status:
  - experimental
browser-compat: api.LanguageDetector
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

رابط **`LanguageDetector`** از {{domxref("Translator and Language Detector APIs", "Translator and Language Detector APIs", "", "nocode")}} شامل تمام عملکردهای تشخیص زبان است؛ از جمله بررسی در دسترس بودن مدل هوش مصنوعی، ایجاد یک نمونه جدید `LanguageDetector`، استفاده از آن برای تشخیص زبان و موارد دیگر.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("LanguageDetector.inputQuota", "inputQuota")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : سهمیه ورودی در دسترس مرورگر برای تشخیص زبان.
- {{domxref("LanguageDetector.expectedInputLanguages", "expectedInputLanguages")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : زبان‌های مورد انتظاری که باید در متن ورودی تشخیص داده شوند.

## متدهای ایستا

- {{domxref("LanguageDetector.availability_static", "availability()")}} {{Experimental_Inline}}
  - : یک مقدار شمارشی برمی‌گرداند که نشان می‌دهد آیا مدل هوش مصنوعی مرورگر از پیکربندی مشخصی از `LanguageDetector` پشتیبانی می‌کند یا خیر.
- {{domxref("LanguageDetector.create_static", "create()")}} {{Experimental_Inline}}
  - : یک نمونه جدید `LanguageDetector` برای تشخیص زبان ایجاد می‌کند.

## متدهای نمونه

- {{domxref("LanguageDetector.destroy", "destroy()")}} {{Experimental_Inline}}
  - : منابع اختصاص‌داده‌شده به نمونه `LanguageDetector` که روی آن فراخوانی شده است را آزاد می‌کند و هر فعالیت بیشتر روی آن را متوقف می‌سازد.
- {{domxref("LanguageDetector.detect", "detect()")}} {{Experimental_Inline}}
  - : نزدیک‌ترین زبان یا زبان‌هایی را که یک رشته متنی به احتمال زیاد با آن‌ها نوشته شده است، تشخیص می‌دهد.
- {{domxref("LanguageDetector.measureInputUsage", "measureInputUsage()")}} {{Experimental_Inline}}
  - : گزارش می‌دهد که یک عملیات تشخیص زبان برای یک ورودی متنی مشخص چقدر از سهمیه ورودی استفاده خواهد کرد.

## مثال‌ها

برای مشاهده یک مثال کامل، به [استفاده از APIهای مترجم و تشخیص زبان](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using) مراجعه کنید.

### ایجاد یک نمونه `LanguageDetector`

```js
const detector = await LanguageDetector.create({
  expectedInputLanguages: ["en-US", "zh"],
});
```

> [!NOTE]
> پیاده‌سازی‌های مختلف احتمالاً از زبان‌های متفاوتی پشتیبانی می‌کنند.

### تشخیص زبان‌ها

```js
const results = await detector.detect(myTextString);

results.forEach((result) => {
  console.log(`${result.detectedLanguage}: ${result.confidence}`);
});

// Results in logs like this:
// la: 0.8359838724136353
// es: 0.017705978825688362
// sv: 0.012977192178368568
// en: 0.011148443445563316
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از APIهای مترجم و تشخیص زبان](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)
```