---
title: "MediaQueryList: addListener() method"
short-title: addListener()
slug: Web/API/MediaQueryList/addListener
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.MediaQueryList.addListener
---

{{APIRef("CSSOM view API")}}{{Deprecated_Header}}

متد منسوخ‌شده‌ی **`addListener()`** از رابط {{DOMxRef("MediaQueryList")}} یک شنونده (listener) به `MediaQueryListener` اضافه می‌کند که در پاسخ به تغییر وضعیت پرسش رسانه‌ای (media query)، یک تابع بازفراخوانی سفارشی را اجرا می‌کند.

در مرورگرهای قدیمی‌تر، `MediaQueryList` هنوز از {{DOMxRef("EventTarget")}} ارث نمی‌برد؛ بنابراین این متد به‌عنوان یک نام مستعار برای {{DOMxRef("EventTarget.addEventListener()")}} ارائه شده بود. اگر `addEventListener()` در مرورگرهایی که باید پشتیبانی کنید موجود است، به‌جای `addListener()` از آن استفاده کنید.

## سینتکس

```js-nolint
addListener(func)
```

### پارامترها

- `func`
  - : یک تابع یا ارجاع به تابع که نشان‌دهنده‌ی تابع بازفراخوانی است که می‌خواهید هنگام تغییر وضعیت پرسش رسانه‌ای اجرا شود.

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
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پرسش‌های رسانه‌ای (Media queries)](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از پرسش‌های رسانه‌ای در کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}