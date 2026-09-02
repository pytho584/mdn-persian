---
title: "MediaQueryList: matches property"
short-title: matches
slug: Web/API/MediaQueryList/matches
page-type: web-api-instance-property
browser-compat: api.MediaQueryList.matches
---

{{APIRef("CSSOM view API")}}

خاصیت فقط‌خواندنی **`matches`** در رابط {{DOMxRef("MediaQueryList")}} یک مقدار بولی است که اگر {{DOMxRef("document")}} در حال حاضر با فهرست رسانه‌ای (media query list) مطابقت داشته باشد `true` و در غیر این صورت `false` برمی‌گرداند.

با گوش دادن به رویداد {{domxref("MediaQueryList.change_event", "change")}} که روی `MediaQueryList` رخ می‌دهد، می‌توانید از تغییر مقدار `matches` مطلع شوید.

## مقدار

یک مقدار بولی که اگر {{DOMxRef("document")}} در حال حاضر با فهرست رسانه‌ای مطابقت داشته باشد `true` است؛ در غیر این صورت `false`.

## مثال‌ها

این مثال با ایجاد یک فهرست رسانه‌ای با استفاده از ویژگی رسانه‌ای {{cssxref("@media/orientation")}} تغییر جهت نمای دید (viewport) را تشخیص می‌دهد:

```js
const mql = window.matchMedia("(orientation:landscape)");
mql.addEventListener("change", (event) => {
  if (event.matches) {
    console.log("Now in landscape orientation");
  } else {
    console.log("Now in portrait orientation");
  }
});
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