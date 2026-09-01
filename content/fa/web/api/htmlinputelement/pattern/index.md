---
title: "HTMLInputElement: pattern property"
short-title: pattern
slug: Web/API/HTMLInputElement/pattern
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.pattern
---

{{ APIRef("HTML DOM") }}

خاصیت **`pattern`** از رابط {{DOMxRef("HTMLInputElement")}} نشان‌دهنده یک [عبارت باقاعده](/en-US/docs/Web/JavaScript/Guide/Regular_expressions) است که یک مقدار غیر null عنصر {{HTMLElement("input")}} باید با آن مطابقت داشته باشد. این ویژگی منعکس‌کننده ویژگی [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern) عنصر {{htmlelement("input")}} است.

خاصیت `pattern` برای انواع `text`، `search`، `url`، `tel`، `email` و `password` معتبر است. این یک عبارت باقاعده تعریف می‌کند که {{DOMxRef("HTMLInputElement.value", "value")}} ورودی باید با آن مطابقت داشته باشد تا مقدار بتواند از [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) عبور کند.

اگر یک مقدار غیر null با محدودیت‌های تعیین‌شده توسط مقدار `pattern` مطابقت نداشته باشد، ویژگی فقط‌خواندنی {{domxref('ValidityState.patternMismatch','patternMismatch')}} از شیء {{domxref('ValidityState')}} برابر با `true` خواهد بود.

## مقدار

یک رشته.

## مثال‌ها

```js
const inputElement = document.getElementById("year");
console.log(input.pattern);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.value")}}
- [اعتبارسنجی سمت کلاینت](/en-US/docs/Web/HTML/Reference/Elements/input#client-side_validation)
- شبه‌کلاس‌های {{CSSXref(":valid")}} و {{CSSXref(":invalid")}}