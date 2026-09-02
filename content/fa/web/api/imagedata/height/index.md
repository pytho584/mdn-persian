---
title: "ImageData: height property"
short-title: height
slug: Web/API/ImageData/height
page-type: web-api-instance-property
browser-compat: api.ImageData.height
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`ImageData.height`** تعداد ردیف‌های موجود در شیء {{domxref("ImageData")}} را برمی‌گرداند.

## مقدار

یک عدد.

## مثال‌ها

این مثال یک شیء `ImageData` به عرض ۲۰۰ پیکسل و ارتفاع ۱۰۰ پیکسل ایجاد می‌کند. بنابراین، ویژگی `height` برابر با `100` است.

```js
let imageData = new ImageData(200, 100);
console.log(imageData.height); // 100
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ImageData.width")}}
- {{domxref("ImageData")}}