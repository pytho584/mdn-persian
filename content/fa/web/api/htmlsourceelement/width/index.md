```markdown
---
title: "HTMLSourceElement: width property"
short-title: width
slug: Web/API/HTMLSourceElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.width
---

{{APIRef("HTML DOM")}}

ویژگی **`width`** در رابط {{domxref("HTMLSourceElement")}} یک عدد غیرمنفی است که عرض منبع تصویر را برحسب پیکسل‌های CSS نشان می‌دهد.

این ویژگی تنها زمانی تأثیر دارد که والد عنصر کنونی {{HTMLElement("source")}} یک عنصر {{HTMLElement("picture")}} باشد.

این ویژگی منعکس‌کنندهٔ ویژگی `width` عنصر {{HTMLElement("source")}} است.

## مقدار

یک عدد غیرمنفی که عرض منبع تصویر را برحسب پیکسل‌های CSS نشان می‌دهد.

## مثال‌ها

```html
<picture id="img">
  <source
    srcset="landscape.png"
    media="(width >= 1000px)"
    width="1000"
    height="400" />
  <source
    srcset="square.png"
    media="(width >= 800px)"
    width="800"
    height="800" />
  <source
    srcset="portrait.png"
    media="(width >= 600px)"
    width="600"
    height="800" />
  <img
    src="fallback.png"
    alt="Image used when the browser does not support the sources"
    width="500"
    height="400" />
</picture>
```

```js
const img = document.getElementById("img");
const sources = img.querySelectorAll("source");
console.log(Array.from(sources).map((el) => el.width)); // Output: [1000, 800, 600]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement.width")}}
- {{domxref("HTMLEmbedElement.width")}}
- {{domxref("HTMLIFrameElement.width")}}
- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLObjectElement.width")}}
- {{domxref("HTMLVideoElement.width")}}
```