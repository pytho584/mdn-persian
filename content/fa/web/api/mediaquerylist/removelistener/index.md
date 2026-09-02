---
title: "MediaQueryList: removeListener() method"
short-title: removeListener()
slug: Web/API/MediaQueryList/removeListener
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.MediaQueryList.removeListener
---

{{APIRef("CSSOM view API")}}{{Deprecated_Header}}

متد **`removeListener()`** در رابط {{DOMxRef("MediaQueryList")}} یک شنونده را از `MediaQueryListener` حذف می‌کند.

در مرورگرهای قدیمی‌تر، `MediaQueryList` هنوز از {{DOMxRef("EventTarget")}} ارث نمی‌برد؛ بنابراین این متد به‌عنوان یک نام مستعار برای {{DOMxRef("EventTarget.removeEventListener()")}} ارائه شده بود. اگر در مرورگرهایی که باید پشتیبانی کنید، `removeEventListener()` در دسترس است، به‌جای `removeListener()` از آن استفاده کنید.

## سینتکس

```js-nolint
removeListener(func)
```

### پارامترها

- `func`
  - : تابع یا ارجاعی به تابع که تابع بازخواستی (callback) مورد نظر شما برای حذف را نشان می‌دهد.

### مقدار بازگشتی

هیچ مقداری ({{jsxref("undefined")}}).

## مثال‌ها

```js
const paragraph = document.querySelector("p");
const mediaQueryList = window.matchMedia("(width <= 600px)");

function screenTest(e) {
  if (e.matches) {
    /* the viewport is 600 pixels wide or less */
    paragraph.textContent = "This is a narrow screen — 600px wide or less.";
    document.body.style.backgroundColor = "pink";
  } else {
    /* the viewport is more than 600 pixels wide */
    paragraph.textContent = "This is a wide screen — more than 600px wide.";
    document.body.style.backgroundColor = "aquamarine";
  }
}

mediaQueryList.addListener(screenTest);

// Later on, when it is no longer needed
mediaQueryList.removeListener(screenTest);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از Media queries در کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}