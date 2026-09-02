---
title: "HTMLVideoElement: height property"
short-title: height
slug: Web/API/HTMLVideoElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLVideoElement.height
---

{{APIRef("HTML DOM")}}

خاصیت **`height`** در رابط {{domxref("HTMLVideoElement")}} یک عدد صحیح را برمی‌گرداند که منعکس‌کنندهٔ ویژگی `height` عنصر {{HTMLElement("video")}} است و ارتفاع نمایشی منبع را بر حسب پیکسل‌های CSS مشخص می‌کند.

## مقدار

یک عدد صحیح مثبت یا ۰.

## مثال‌ها

```html
<video id="media" width="800" height="600"></video>
```

```js
const el = document.getElementById("media");
console.log(el.height); // Output: 600
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.height")}}
- {{domxref("HTMLEmbedElement.height")}}
- {{domxref("HTMLIFrameElement.height")}}
- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLObjectElement.height")}}
- {{domxref("HTMLSourceElement.height")}}