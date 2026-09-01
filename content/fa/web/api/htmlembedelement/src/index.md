---
title: "HTMLEmbedElement: src property"
short-title: src
slug: Web/API/HTMLEmbedElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLEmbedElement.src
---

{{APIRef("HTML DOM")}}

ویژگی **`src`** از رابط {{domxref("HTMLEmbedElement")}} یک رشته را برمی‌گرداند که نشانی اینترنتی (URL) منبع جاسازی‌شده را نشان می‌دهد.

این ویژگی منعکس‌کنندهٔ ویژگی `src` عنصر {{HTMLElement("embed")}} است.

## مقدار

یک رشته.

## مثال‌ها

```html
<embed
  id="el"
  type="video/quicktime"
  src="movie.mov"
  width="640"
  height="480"
  title="Title of my video" />
```

```js
const el = document.getElementById("el");
console.log(el.src); // Output: "movie.mov"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}