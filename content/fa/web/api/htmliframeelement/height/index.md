---
title: "HTMLIFrameElement: height property"
short-title: height
slug: Web/API/HTMLIFrameElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.height
---

{{APIRef("HTML DOM")}}

خاصیت **`height`** از رابط {{domxref("HTMLIFrameElement")}} یک رشته را برمی‌گرداند که منعکس‌کنندهٔ ویژگی `height` عنصر {{HTMLElement("iframe")}} است و ارتفاع فریم را بر حسب پیکسل‌های CSS نشان می‌دهد.

## مقدار

یک رشته که ارتفاع فریم را بر حسب پیکسل‌های CSS نشان می‌دهد.

## مثال‌ها

```html
<iframe id="el" width="800" height="600"></iframe>
```

```js
const el = document.getElementById("el");
console.log(el.height); // Output: '600'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.height")}}
- {{domxref("HTMLEmbedElement.height")}}
- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLObjectElement.height")}}
- {{domxref("HTMLSourceElement.height")}}
- {{domxref("HTMLVideoElement.height")}}