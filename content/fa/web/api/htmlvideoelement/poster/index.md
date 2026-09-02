---
title: "HTMLVideoElement: poster property"
short-title: poster
slug: Web/API/HTMLVideoElement/poster
page-type: web-api-instance-property
browser-compat: api.HTMLVideoElement.poster
---

{{APIRef("HTML DOM")}}

ویژگی **`poster`** در رابط {{domxref("HTMLVideoElement")}} رشته‌ای است که نشانی اینترنتی (URL) تصویری را بازتاب می‌دهد که هنگام نبودِ داده ویدیویی نمایش داده می‌شود. اگر این ویژگی نشانی اینترنتی معتبری را نشان ندهد، هیچ فریم پوستری (poster frame) نمایش داده نخواهد شد.

این ویژگی، مشخصه (attribute) `poster` عنصر {{HTMLElement("video")}} را بازتاب می‌دهد.

## مقدار

یک رشته (string).

## مثال‌ها

```html
<video
  id="media"
  src="https://example.com/video.mp4"
  poster="https://example.com/poster.jpg"></video>
```

```js
const el = document.getElementById("media");
console.log(el.poster); // Output: "https://example.com/poster.jpg"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
