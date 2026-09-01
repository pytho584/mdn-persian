---
title: "HTMLIFrameElement: width property"
short-title: width
slug: Web/API/HTMLIFrameElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.width
---

{{APIRef("HTML DOM")}}

ویژگی **`width`** از رابط {{domxref("HTMLIFrameElement")}} یک رشته را برمی‌گرداند که منعکس‌کنندهٔ ویژگی `width` عنصر {{HTMLElement("iframe")}} است و عرض فریم را بر حسب پیکسل‌های CSS نشان می‌دهد.

## مقدار

یک رشته که عرض فریم را بر حسب پیکسل‌های CSS نشان می‌دهد.

## مثال‌ها

```html
<iframe id="el" width="800" height="600"></iframe>
```

```js
const el = document.getElementById("el");
console.log(el.width); // Output: '800'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.width")}}
- {{domxref("HTMLEmbedElement.width")}}
- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLObjectElement.width")}}
- {{domxref("HTMLSourceElement.width")}}
- {{domxref("HTMLVideoElement.width")}}