---
title: "HTMLInputElement: step property"
---

---
title: "HTMLInputElement: step property"
short-title: step
slug: Web/API/HTMLInputElement/step
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.step
---

{{ApiRef("HTML DOM")}}

ویژگی **`step`** در واسط {{domxref("HTMLInputElement")}} مشخص می‌کند که عناصر {{HTMLElement("input")}} عددی یا تاریخ-زمان با چه گامی می‌توانند تغییر کنند. این ویژگی منعکس‌کنندهٔ ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) عنصر است. مقادیر معتبر شامل رشتهٔ `"any"` یا رشته‌ای حاوی یک عدد ممیز شناور مثبت است. اگر ویژگی به صراحت تنظیم نشده باشد، ویژگی `step` یک رشتهٔ خالی است.

## مقدار

یک رشته که نشان‌دهندهٔ مقدار `step` عنصر است، یا اگر هیچ گامی به صراحت تنظیم نشده باشد، یک رشتهٔ خالی.

## مثال

```js
const inputElement = document.querySelector('[type="number"]');
console.log(inputElement.step); // the current value of the step attribute
inputElement.step = 0.1; // sets the step value to "0.1"
inputElement.step = "any"; // sets the step to "any"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}} از نوع {{HTMLElement("input/range", "range")}}، {{HTMLElement("input/number", "number")}}، {{HTMLElement("input/date", "date")}}، {{HTMLElement("input/month", "month")}}، {{HTMLElement("input/week", "week")}} و {{HTMLElement("input/time", "time")}}
- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.type")}}