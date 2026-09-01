---
title: "HTMLInputElement: min property"
short-title: min
slug: Web/API/HTMLInputElement/min
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.min
---

{{ApiRef("HTML DOM")}}

ویژگی **`min`** از رابط {{domxref("HTMLInputElement")}} منعکس‌کنندهٔ ویژگی [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) عنصر {{HTMLElement("input")}} است که به‌طور کلی حداقل مقدار معتبر را برای یک ورودی عددی یا تاریخ-زمان تعریف می‌کند. اگر ویژگی به‌طور صریح تنظیم نشده باشد، ویژگی `min` یک رشتهٔ خالی است.

## مقدار

یک رشته که مقدار `min` عنصر را نشان می‌دهد یا یک رشتهٔ خالی اگر `min` به‌طور صریح تنظیم نشده باشد.

## مثال

```js
const inputElement = document.querySelector("#range");
console.log(inputElement.min); // the current value of the min attribute
inputElement.min = 0; // sets the min value to "0"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}} از نوع {{HTMLElement("input/range", "range")}}، {{HTMLElement("input/number", "number")}}، {{HTMLElement("input/date", "date")}}، {{HTMLElement("input/month", "month")}}، {{HTMLElement("input/week", "week")}} و {{HTMLElement("input/time", "time")}}
- {{domxref("HTMLInputElement.max")}}
- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.type")}}