---
title: "HTMLVideoElement: width property"
short-title: width
slug: Web/API/HTMLVideoElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLVideoElement.width
---

{{APIRef("HTML DOM")}}

ویژگی **`width`** در رابط {{domxref("HTMLVideoElement")}} یک عدد صحیح برمی‌گرداند که مشخصهٔ `width` عنصر {{HTMLElement("video")}} را بازتاب می‌دهد و عرض نمایشی منبع را بر حسب پیکسل CSS مشخص می‌کند.

## مقدار

یک عدد صحیح مثبت یا 0.

## مثال‌ها

```html
<video id="media" width="800" height="600"></video>
```

```js
const el = document.getElementById("media");
console.log(el.width); // Output: 800
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLCanvasElement.width")}}
- {{domxref("HTMLEmbedElement.width")}}
- {{domxref("HTMLIFrameElement.width")}}
- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLObjectElement.width")}}
- {{domxref("HTMLSourceElement.width")}}
