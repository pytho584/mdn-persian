---
title: "BarcodeDetector: BarcodeDetector() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BarcodeDetector/BarcodeDetector"
translated_by: "n8n + AI"
---

---
title: "BarcodeDetector: BarcodeDetector() constructor"
short-title: BarcodeDetector()
slug: Web/API/BarcodeDetector/BarcodeDetector
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.BarcodeDetector.BarcodeDetector
---

{{securecontext_header}}{{APIRef("Barcode Detector API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

سازندهٔ **`BarcodeDetector()`** یک شیء جدید از {{domxref("BarcodeDetector")}} می‌سازد که بارکدهای خطی و دوبعدی را در تصاویر شناسایی می‌کند.

## نحو

```js-nolint
new BarcodeDetector()
new BarcodeDetector(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها حاوی مجموعه‌ای از `BarcodeFormats` برای جستجو در فراخوانی‌های بعدی {{domxref('BarcodeDetector.detect()','detect()')}} است. گزینه‌ها شامل:
    - `formats` {{optional_inline}}
      - : یک {{jsxref('Array')}} از قالب‌های بارکد به‌صورت رشته. اگر ارائه نشود، فراخوانی‌های `detect()` همهٔ قالب‌های پشتیبانی‌شده را جستجو می‌کنند. بنابراین به دلایل کارایی توصیه می‌شود به قالب‌های خاص محدود شود. برای مشاهدهٔ فهرست کامل قالب‌های پشتیبانی‌شده، به [قالب‌های بارکد پشتیبانی‌شده](/en-US/docs/Web/API/Barcode_Detection_API#supported_barcode_formats) مراجعه کنید.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `formats` مشخص شده باشد و پارامتر خالی یا شامل `unknown` باشد، پرتاب می‌شود.

## مثال‌ها

این مثال یک شیء جدید تشخیص بارکد با قالب‌های پشتیبانی‌شدهٔ مشخص می‌سازد و سازگاری مرورگر را آزمایش می‌کند.

```js
// check compatibility
if (!("BarcodeDetector" in globalThis)) {
  console.log("Barcode Detector is not supported by this browser.");
} else {
  console.log("Barcode Detector supported!");

  // create new detector
  const barcodeDetector = new BarcodeDetector({
    formats: ["code_39", "codabar", "ean_13"],
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}