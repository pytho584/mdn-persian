---
title: "HTMLSourceElement: srcset property"
short-title: srcset
slug: Web/API/HTMLSourceElement/srcset
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.srcset
---

{{APIRef("HTML DOM")}}

ویژگی **`srcset`** در رابط {{domxref("HTMLSourceElement")}} یک رشته است که فهرستی از تصاویر نامزد (candidate images) را با جداسازی کاما در خود دارد.

هر تصویر نامزد شامل URL یک منبع تصویری است که به‌عنوان منبع عنصر استفاده می‌شود و به‌صورت اختیاری یک توصیفگر (descriptor) دارد که شرایط استفاده از آن تصویر را مشخص می‌کند. این توصیفگر یا یک عدد است که بعد از آن `'w'` می‌آید (نشان‌دهنده عرض عنصر) و یا یک عدد است که بعد از آن `'x'` می‌آید (نشان‌دهنده تراکم پیکسلی دستگاه).

این ویژگی منعکس‌کننده ویژگی `srcset` در عنصر {{HTMLElement("source")}} است که درون یک عنصر {{htmlelement("picture")}} قرار می‌گیرد. زمانی که عنصر `source` درون یک عنصر {{htmlelement("audio")}} یا {{htmlelement("video")}} قرار داشته باشد، این ویژگی هیچ معنایی ندارد و نادیده گرفته می‌شود؛ این عناصر در عوض از ویژگی {{domxref("HTMLSourceElement.src", "src")}} استفاده می‌کنند.

## مقدار

یک رشته.

## مثال‌ها

```html
<picture>
  <source
    id="el"
    srcset="smile.png, smile-1.5x.png 1.5x, smile-2x.png 2x"
    type="image/png" />
</picture>
```

```js
const el = document.getElementById("el");
console.log(el.srcset); // Output: "smile.png, smile-1.5x.png 1.5x, smile-large 800w"
el.srcset = "smile.png, smile-med.png 600w, smile-large.png 800w"; // Updates the srcset value
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSourceElement.type")}}
- {{domxref("HTMLSourceElement.src")}}
- {{domxref("HTMLSourceElement.media")}}
- {{domxref("HTMLSourceElement.sizes")}}
- {{htmlelement("source")}}
- {{htmlelement("picture")}}