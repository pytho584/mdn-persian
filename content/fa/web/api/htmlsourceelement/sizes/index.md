---
title: "HTMLSourceElement: sizes property"
short-title: sizes
slug: Web/API/HTMLSourceElement/sizes
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.sizes
---

{{APIRef("HTML DOM")}}

خاصیت **`sizes`** از رابط {{domxref("HTMLSourceElement")}} یک رشته است که فهرستی از یک یا چند اندازه را نشان می‌دهد. این اندازه‌ها بیانگر ابعاد بین نقاط شکست (breakpoints) هستند که منبع به آن‌ها اعمال می‌شود.

این خاصیت، ویژگی `sizes` عنصر {{HTMLElement("source")}} را منعکس می‌کند.

## مقدار

یک رشته.

## مثال‌ها

```html
<picture>
  <source
    id="el"
    srcset="medium-pic.jpg"
    type="image/jpeg"
    sizes="(50em <= width <= 60px) 50em,
           (30em <= width < 50em) 30em" />
</picture>
```

```js
const el = document.getElementById("el");
console.log(el.sizes); // Output: "(50em <= width <= 60px) 50em, (30em <= width < 50em) 30em"
el.sizes = "(50em <= width <= 60px) 100em, (30em <= width < 50em) 60em"; // Updates the sizes value
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.sizes")}}
- {{domxref("HTMLSourceElement.media")}}
- {{domxref("HTMLSourceElement.type")}}
- {{domxref("HTMLSourceElement.src")}}
- {{domxref("HTMLSourceElement.srcset")}}
- {{htmlelement("source")}}
- {{htmlelement("picture")}}
- {{htmlelement("audio")}}
- {{htmlelement("video")}}