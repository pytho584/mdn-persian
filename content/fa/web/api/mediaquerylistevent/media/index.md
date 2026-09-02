---
title: "MediaQueryListEvent: media property"
short-title: media
slug: Web/API/MediaQueryListEvent/media
page-type: web-api-instance-property
browser-compat: api.MediaQueryListEvent.media
---

{{APIRef("CSSOM view API")}}

ویژگی **`media`** از رابط {{DOMxRef("MediaQueryListEvent")}}، یک رشته است که یک media query سریال‌شده را نشان می‌دهد.

## مقدار

یک رشته که نمایانگر یک media query سریال‌شده است.

## نمونه‌ها

```js
const para = document.querySelector("p"); // This is the UI element where to display the text
const mql = window.matchMedia("(width <= 600px)");

mql.addEventListener("change", (event) => {
  if (event.matches) {
    // The viewport is 600 pixels wide or less
    para.textContent = "This is a narrow screen — less than 600px wide.";
    document.body.style.backgroundColor = "red";
  } else {
    // The viewport is more than 600 pixels wide
    para.textContent = "This is a wide screen — more than 600px wide.";
    document.body.style.backgroundColor = "blue";
  }

  console.log(event.media);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پرس‌وجوهای رسانه‌ای](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از media queries در کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}