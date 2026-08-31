---
title: "BarcodeDetector"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BarcodeDetector"
translated_by: "n8n + AI"
---

---
title: BarcodeDetector
slug: Web/API/BarcodeDetector
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BarcodeDetector
---

{{securecontext_header}}{{APIRef("Barcode Detector API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

رابط **`BarcodeDetector`** از {{domxref('Barcode Detection API', '', '', 'nocode')}} امکان تشخیص بارکدهای خطی و دوبعدی را در تصاویر فراهم می‌کند.

## سازنده‌ها

- {{domxref('BarcodeDetector.BarcodeDetector', 'BarcodeDetector.BarcodeDetector()')}} {{Experimental_Inline}}
  - : یک شیء `BarcodeDetector` را با `BarcodeDetectorOptions` اختیاری ایجاد و بازمی‌گرداند.

## متدهای ایستا

- {{domxref('BarcodeDetector/getSupportedFormats_static', 'getSupportedFormats()')}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} را برمی‌گرداند که با یک {{jsxref('Array')}} از [barcode format types](/en-US/docs/Web/API/Barcode_Detection_API#supported_barcode_formats) پشتیبانی‌شده تکمیل می‌شود.

## متدهای نمونه

- {{domxref('BarcodeDetector.detect', 'detect()')}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} را برمی‌گرداند که با آرایه‌ای از اشیاء `DetectedBarcode` با ویژگی‌های زیر تکمیل می‌شود:
    - `boundingBox`: یک {{domxref('DOMRectReadOnly')}} که ابعاد یک مستطیل را برمی‌گرداند که گستره‌ی بارکد شناسایی‌شده را نشان می‌دهد و با تصویر هم‌راستا است.
    - `cornerPoints`: مختصات x و y چهار گوشه‌ی بارکد شناسایی‌شده نسبت به تصویر، که از بالا چپ شروع شده و در جهت عقربه‌های ساعت حرکت می‌کند. این نقاط ممکن است به دلیل اعوجاج‌های پرسپکتیو در تصویر مربع نباشند.
    - `format`: قالب بارکد شناسایی‌شده. (برای فهرست کامل قالب‌ها، به فهرست [supported barcode format](/en-US/docs/Web/API/Barcode_Detection_API#supported_barcode_formats) مراجعه کنید.)
    - `rawValue`: یک رشته که از داده‌های بارکد رمزگشایی شده است.

## مثال‌ها

### ایجاد یک آشکارساز

این مثال یک شیء جدید تشخیص بارکد، با قالب‌های پشتیبانی‌شده‌ی مشخص‌شده ایجاد می‌کند و سازگاری مرورگر را آزمایش می‌کند.

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

### دریافت قالب‌های پشتیبانی‌شده

مثال زیر متد ایستا `getSupportedFormats()` را فراخوانی می‌کند و نتایج را در کنسول ثبت می‌کند.

```js
// check supported types
BarcodeDetector.getSupportedFormats().then((supportedFormats) => {
  supportedFormats.forEach((format) => console.log(format));
});
```

### تشخیص بارکدها

این مثال از متد `detect()` برای شناسایی بارکدهای موجود در تصویر داده‌شده استفاده می‌کند. این بارکدها پیمایش می‌شوند و داده‌های بارکد در کنسول ثبت می‌شوند.

```js
barcodeDetector
  .detect(imageEl)
  .then((barcodes) => {
    barcodes.forEach((barcode) => console.log(barcode.rawValue));
  })
  .catch((err) => {
    console.log(err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [barcodefaq.com: A website with information about different barcodes and examples of the different types.](https://www.barcodefaq.com/)
- [Accelerated Shape Detection in Images](https://developer.chrome.com/docs/capabilities/shape-detection#barcodedetector)