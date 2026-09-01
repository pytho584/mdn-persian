---
title: "HTMLEmbedElement: width property"
short-title: width
slug: Web/API/HTMLEmbedElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLEmbedElement.width
---

{{APIRef("HTML DOM")}}

ویژگی **`width`** در رابط {{domxref("HTMLEmbedElement")}} یک رشته برمی‌گرداند که منعکس‌کنندهٔ صفت `width` عنصر {{HTMLElement("embed")}} است و عرض نمایش‌داده‌شدهٔ منبع را برحسب پیکسل‌های CSS مشخص می‌کند.

## مقدار

یک رشته که عرض نمایش‌داده‌شدهٔ منبع را در پیکسل‌های CSS نشان می‌دهد.

## مثال‌ها

```html
<embed id="el" width="800" height="600" src="https://example.com" />
```

```js
const el = document.getElementById("el");
console.log(el.width); // Output: '800'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.width")}}
- {{domxref("HTMLIFrameElement.width")}}
- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLObjectElement.width")}}
- {{domxref("HTMLSourceElement.width")}}
- {{domxref("HTMLVideoElement.width")}}