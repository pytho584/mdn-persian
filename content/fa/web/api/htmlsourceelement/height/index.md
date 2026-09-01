---
title: "HTMLSourceElement: height property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLSourceElement/height"
---

---
title: "HTMLSourceElement: height property"
short-title: height
slug: Web/API/HTMLSourceElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.height
---

{{APIRef("HTML DOM")}}

ویژگی **`height`** در رابط {{domxref("HTMLSourceElement")}} یک عدد نامنفی است که ارتفاع منبع تصویر را بر حسب پیکسل CSS نشان می‌دهد.

این ویژگی فقط زمانی اثر دارد که والد عنصر فعلی {{HTMLElement("source")}} یک عنصر {{HTMLElement("picture")}} باشد.

این ویژگی منعکس‌کنندهٔ ویژگی `height` عنصر {{HTMLElement("source")}} است.

## مقدار

یک عدد نامنفی که ارتفاع منبع تصویر را بر حسب پیکسل CSS نشان می‌دهد.

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
console.log(Array.from(sources).map((el) => el.height)); // Output: [400, 800, 800]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLCanvasElement.height")}}
- {{domxref("HTMLEmbedElement.height")}}
- {{domxref("HTMLIFrameElement.height")}}
- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLObjectElement.height")}}
- {{domxref("HTMLVideoElement.height")}}