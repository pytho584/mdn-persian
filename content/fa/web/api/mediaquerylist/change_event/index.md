---
title: "MediaQueryList: change event"
short-title: change
slug: Web/API/MediaQueryList/change_event
page-type: web-api-event
browser-compat: api.MediaQueryList.change_event
---

{{APIRef("CSSOM view API")}}

رویداد **`change`** از رابط {{DOMxRef("MediaQueryList")}} زمانی رخ می‌دهد که وضعیت پشتیبانی از رسانه (media query) تغییر کند.

## نحو (Syntax)

می‌توانید از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("MediaQueryListEvent")}}. این رویداد از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MediaQueryListEvent")}}

## مثال

```js
const mql = window.matchMedia("(width <= 600px)");

mql.onchange = (e) => {
  if (e.matches) {
    /* viewport حداکثر ۶۰۰ پیکسل عرض دارد */
    console.log("This is a narrow screen — less than 600px wide.");
  } else {
    /* viewport بیشتر از ۶۰۰ پیکسل عرض دارد */
    console.log("This is a wide screen — more than 600px wide.");
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [Using media queries from code](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}