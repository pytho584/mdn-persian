---
title: "MediaQueryListEvent: matches property"
short-title: matches
slug: Web/API/MediaQueryListEvent/matches
page-type: web-api-instance-property
browser-compat: api.MediaQueryListEvent.matches
---

{{APIRef("CSSOM view API")}}

خاصیت فقط‑خواندنی **`matches`** از رابط {{DOMxRef("MediaQueryListEvent")}} یک مقدار بولین است که اگر {{DOMxRef("document")}} در حال حاضر با لیست پرس‌وجوی رسانه مطابقت داشته باشد، `true` و در غیر این صورت `false` است.

## مقدار

یک مقدار بولین؛ اگر {{DOMxRef("document")}} در حال حاضر با لیست پرس‌وجوی رسانه مطابقت داشته باشد `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

```js
const para = document.querySelector("p"); // این عنصر UI است که متن در آن نمایش داده می‌شود
const mql = window.matchMedia("(width <= 600px)");

mql.addEventListener("change", (event) => {
  if (event.matches) {
    // viewport ۶۰۰ پیکسل یا کمتر عرض دارد
    para.textContent = "این یک صفحه‌نمایش باریک است — کمتر از ۶۰۰ پیکسل عرض.";
    document.body.style.backgroundColor = "red";
  } else {
    // viewport بیش از ۶۰۰ پیکسل عرض دارد
    para.textContent = "این یک صفحه‌نمایش عریض است — بیش از ۶۰۰ پیکسل عرض.";
    document.body.style.backgroundColor = "blue";
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پرس‌وجوهای رسانه](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از پرس‌وجوهای رسانه در کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}