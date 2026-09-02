---
title: MediaQueryListEvent
slug: Web/API/MediaQueryListEvent
page-type: web-api-interface
browser-compat: api.MediaQueryListEvent
---

{{APIRef("CSSOM view API")}}

شیء `MediaQueryListEvent` اطلاعات مربوط به تغییراتی را که در یک شیء {{DOMxRef("MediaQueryList")}} رخ داده است ذخیره می‌کند — نمونه‌های آن به عنوان شیء رویداد در تابعی که توسط یک رویداد {{DOMxRef("MediaQueryList.change_event", "change")}} ارجاع داده می‌شود در دسترس هستند.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{DOMxRef("MediaQueryListEvent.MediaQueryListEvent()", "MediaQueryListEvent()")}}
  - : یک نمونه جدید از `MediaQueryListEvent` ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

_رابط `MediaQueryListEvent` ویژگی‌ها را از رابط والد خود، یعنی {{DOMxRef("Event")}}، به ارث می‌برد._

- {{DOMxRef("MediaQueryListEvent.matches")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که اگر {{DOMxRef("document")}} در حال حاضر با لیست پرس‌وجوی رسانه مطابقت داشته باشد `true` است و در غیر این صورت `false`.
- {{DOMxRef("MediaQueryListEvent.media")}} {{ReadOnlyInline}}
  - : یک رشته که یک پرس‌وجوی رسانه سریالی‌شده را نمایش می‌دهد.

## روش‌های نمونه (Instance methods)

_رابط `MediaQueryListEvent` روش‌ها را از رابط والد خود، یعنی {{DOMxRef("Event")}}، به ارث می‌برد._

## مثال‌ها

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
});
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [پرس‌وجوهای رسانه (Media queries)](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از پرس‌وجوهای رسانه از طریق کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}