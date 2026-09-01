---
title: "HTMLInputElement: max property"
short-title: max
slug: Web/API/HTMLInputElement/max
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.max
---

{{ApiRef("HTML DOM")}}

خاصیت **`max`** از رابط {{domxref("HTMLInputElement")}} منعکس‌کننده ویژگی [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) عنصر {{HTMLElement("input")}} است که به طور کلی حداکثر مقدار معتبر برای یک ورودی عددی یا تاریخ-زمان را تعریف می‌کند. اگر این ویژگی به صراحت تنظیم نشده باشد، خاصیت `max` یک رشته خالی است.

## مقدار

یک رشته که مقدار `max` عنصر را نمایش می‌دهد، یا یک رشته خالی اگر `max` به صراحت تنظیم نشده باشد.

## مثال

```js
const inputElement = document.querySelector("#time");
console.log(inputElement.max); // the current value of the max attribute
inputElement.max = "18:00:00"; // sets the max value to 6pm
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}} از نوع {{HTMLElement("input/range", "range")}}, {{HTMLElement("input/number", "number")}}, {{HTMLElement("input/date", "date")}}, {{HTMLElement("input/month", "month")}}, {{HTMLElement("input/week", "week")}}, و {{HTMLElement("input/time", "time")}}
- {{domxref("HTMLInputElement.min")}}
- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.type")}}