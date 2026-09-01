---
title: "HTMLMediaElement: currentSrc property"
short-title: currentSrc
slug: Web/API/HTMLMediaElement/currentSrc
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.currentSrc
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.currentSrc`** شامل URL مطلق منبع رسانهای انتخاب‌شده است. این حالت می‌تواند برای مثال زمانی رخ دهد که وب‌سرور یک فایل رسانه‌ای را بر اساس وضوح نمایشگر کاربر انتخاب کند. اگر ویژگی `networkState` برابر با `EMPTY` باشد، مقدار این ویژگی یک رشتهٔ خالی است.

## مقدار

یک رشته که شامل URL مطلق منبع رسانه‌ای انتخاب‌شده است؛ اگر `networkState` برابر با `EMPTY` باشد، این مقدار می‌تواند یک رشتهٔ خالی باشد؛ در غیر این صورت، این مقدار یکی از منابع فهرست‌شده توسط {{domxref("HTMLSourceElement")}} موجود در داخل عنصر رسانه‌ای، یا مقدار {{domxref("HTMLMediaElement.src", "src")}} خواهد بود، در صورتی که هیچ عنصر {{HTMLElement("source")}} ارائه نشده باشد.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.currentSrc); // ""
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف ویژگی `HTMLMediaElement.currentSrc` استفاده می‌شود.