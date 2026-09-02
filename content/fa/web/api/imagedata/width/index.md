---
title: "ImageData: width property"
short-title: width
slug: Web/API/ImageData/width
page-type: web-api-instance-property
browser-compat: api.ImageData.width
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`ImageData.width`** تعداد پیکسل‌های هر ردیف را در شیء {{domxref("ImageData")}} برمی‌گرداند.

## مقدار

یک عدد.

## مثال

این مثال یک شیء `ImageData` به عرض ۲۰۰ پیکسل و ارتفاع ۱۰۰ پیکسل ایجاد می‌کند. بنابراین، ویژگی `width` برابر با ۲۰۰ است.

```js
let imageData = new ImageData(200, 100);
console.log(imageData.width); // 200
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ImageData.height")}}
- {{domxref("ImageData")}}