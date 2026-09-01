---
title: "HTMLImageElement: currentSrc property"
short-title: currentSrc
slug: Web/API/HTMLImageElement/currentSrc
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.currentSrc
---

{{APIRef("HTML DOM")}}

خاصیت فقط خواندنی **`currentSrc`** از رابط {{domxref("HTMLImageElement")}}، نشانی اینترنتی (URL) تصویری را که مرورگر برای بارگذاری انتخاب کرده است، نشان می‌دهد.

## مقدار

یک رشته که نشانی کامل اینترنتی تصویری را که در حال حاضر توسط مرورگر برای بارگذاری انتخاب شده است، نشان می‌دهد. اگر تصویر از ویژگی {{domxref("HTMLImageElement.srcset", "srcset")}} استفاده کند، `currentSrc` به شما امکان می‌دهد تعیین کنید کدام تصویر از میان مجموعه تصاویر ارائه‌شده توسط مرورگر انتخاب شده است. مقدار این ویژگی ربطی به موفقیت‌آمیز بودن بارگذاری تصویر ندارد.

## مثال‌ها

### آزمایش اینکه کدام تصویر بارگذاری شده است

در این مثال، دو اندازه متفاوت برای یک تصویر از یک ساعت ارائه شده است. یکی ۲۰۰ پیکسل عرض و دیگری ۴۰۰ پیکسل عرض دارد. ویژگی [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) برای مشخص کردن اینکه اگر viewport کمتر از ۴۰۰ پیکسل عرض داشته باشد، تصویر باید با ۵۰٪ عرض سند رسم شود، و در غیر این صورت با ۹۰٪ عرض سند رسم شود، ارائه شده است.

#### HTML

```html
<img
  src="/en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-400px.png"
  alt="Clock"
  srcset="
    /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-200px.png 200w,
    /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-400px.png 400w
  "
  sizes="(width <= 400px) 50%, 90%" />
```

#### JavaScript

```js
const clockImage = document.querySelector("img");
const p = document.createElement("p");

p.textContent = clockImage.currentSrc.endsWith("200px.png")
  ? "Using the 200px image!"
  : "Using the 400px image.";
document.body.appendChild(p);
```

#### نتیجه

{{EmbedLiveSample("Testing which image is loaded", 640, 370)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.src")}}
- {{domxref("HTMLImageElement.srcSet")}}