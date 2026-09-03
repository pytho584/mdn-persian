---
title: "Navigator: pdfViewerEnabled property"
---

---
title: "Navigator: pdfViewerEnabled property"
short-title: pdfViewerEnabled
slug: Web/API/Navigator/pdfViewerEnabled
page-type: web-api-instance-property
browser-compat: api.Navigator.pdfViewerEnabled
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`pdfViewerEnabled`** در رابط {{domxref("Navigator")}} مشخص می‌کند که آیا مرورگر هنگام پیمایش به فایل‌های PDF، نمایش درون‌خطی آن‌ها را پشتیبانی می‌کند یا نه.

اگر نمایش درون‌خطی پشتیبانی نشود، فایل PDF دانلود می‌شود و ممکن است سپس توسط یک برنامهٔ خارجی مدیریت شود.

> [!NOTE]
> این ویژگی جایگزین چند روش قدیمی برای تشخیص پشتیبانی از نمایش درون‌خطی فایل‌های PDF است.

## مقدار

اگر مرورگر هنگام پیمایش به فایل بتواند فایل PDF را به‌صورت درون‌خطی نمایش دهد (چه با نمایشگر داخلی و چه با افزونهٔ نمایشگر PDF)، مقدار `true` است؛ در غیر این صورت `false`.

## مثال‌ها

برای بررسی پشتیبانی از نمایش درون‌خطی PDF:

```js
if (!navigator.pdfViewerEnabled) {
  // The browser does not support inline viewing of PDF files.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
