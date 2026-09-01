---
title: "HTMLEmbedElement: height property"
short-title: height
slug: Web/API/HTMLEmbedElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLEmbedElement.height
---

{{APIRef("HTML DOM")}}

ویژگی **`height`** در رابط {{domxref("HTMLEmbedElement")}} رشته‌ای را برمی‌گرداند که منعکس‌کنندهٔ ویژگی `height` عنصر {{HTMLElement("embed")}} است و ارتفاع نمایش‌داده‌شدهٔ منبع را بر حسب پیکسل CSS نشان می‌دهد.

## مقدار

رشته‌ای که ارتفاع نمایش‌داده‌شدهٔ منبع را بر حسب پیکسل CSS نشان می‌دهد.

## مثال‌ها

```html
<embed id="el" width="800" height="600" src="https://example.com" />
```

```js
const el = document.getElementById("el");
console.log(el.height); // خروجی: '600'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.height")}}
- {{domxref("HTMLIFrameElement.height")}}
- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLObjectElement.height")}}
- {{domxref("HTMLSourceElement.height")}}
- {{domxref("HTMLVideoElement.height")}}