---
title: "HTMLSourceElement: src property"
short-title: src
slug: Web/API/HTMLSourceElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.src
---

{{APIRef("HTML DOM")}}

خصوصیت **`src`** در رابط {{domxref("HTMLSourceElement")}} یک رشته است که URL یک منبع رسانه‌ای را برای استفاده به عنوان منبع عنصر مشخص می‌کند.

این خصوصیت منعکس‌کننده ویژگی `src` عنصر {{HTMLElement("source")}} است که درون یک عنصر {{htmlelement("audio")}} یا {{htmlelement("video")}} قرار گرفته است. وقتی درون یک عنصر {{htmlelement("picture")}} قرار گیرد، معنی ندارد و نادیده گرفته می‌شود.

## مقدار

یک رشته؛ URL منبعی که در عنصر استفاده می‌شود.

## مثال‌ها

```html
<video>
  <source
    id="el"
    src="large.webp"
    type="video/webp"
    media="screen and (600px <= width <= 800px)" />
</video>
```

```js
const el = document.getElementById("el");
console.log(el.src); // Output: "large.webp"
el.src = "medium.webp"; // Updates the src value
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSourceElement.type")}}
- {{domxref("HTMLSourceElement.srcset")}}
- {{domxref("HTMLSourceElement.media")}}
- {{domxref("HTMLSourceElement.sizes")}}
- {{htmlelement("source")}}
- {{htmlelement("audio")}}
- {{htmlelement("video")}}