---
title: "HTMLSourceElement: media property"
short-title: media
slug: Web/API/HTMLSourceElement/media
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.media
---

{{APIRef("HTML DOM")}}

ویژگی **`media`** از رابط {{domxref("HTMLSourceElement")}} یک رشته است که رسانهٔ مقصدِ در نظر گرفته‌شده برای منبع را مشخص می‌کند. مقدار آن یک [media query](/en-US/docs/Web/CSS/Guides/Media_queries/Using) است؛ فهرستی از انواع رسانه، ویژگی‌های رسانه و عملگرهای منطقی که با کاما از هم جدا می‌شوند.

این ویژگی منعکس‌کنندهٔ ویژگی `media` عنصر {{HTMLElement("source")}} است.

## مقدار

یک رشته.

## مثال‌ها

```html
<video>
  <source
    id="el"
    src="largeVideo.mov"
    type="video/quicktime"
    media="screen and (width >= 600px)" />
</video>
```

```js
const el = document.getElementById("el");
console.log(el.media); // Output: "screen and (width >= 600px)"
el.media = "(width >= 800px)"; // Updates the media value
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSourceElement.type")}}
- {{domxref("HTMLSourceElement.sizes")}}
- {{domxref("HTMLSourceElement.src")}}
- {{domxref("HTMLSourceElement.srcset")}}
- {{htmlelement("source")}}
- {{htmlelement("picture")}}
- {{htmlelement("audio")}}
- {{htmlelement("video")}}
- [Using media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Using)