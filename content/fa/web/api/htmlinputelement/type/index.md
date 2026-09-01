---
title: "HTMLInputElement: type property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/type"
---

---
title: "HTMLInputElement: type property"
short-title: type
slug: Web/API/HTMLInputElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.type
---

{{ApiRef("HTML DOM")}}

خاصیت **`type`** از رابط {{domxref("HTMLInputElement")}} مشخص می‌کند که چه نوع داده‌ای در عنصر {{HTMLElement("input")}} مجاز است، مثلاً یک عدد، یک تاریخ یا یک ایمیل. مرورگرها برای کمک به کاربر در وارد کردن یک مقدار معتبر، ابزار و رفتار مناسب را انتخاب می‌کنند.

این خاصیت منعکس‌کنندهٔ ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) عنصر {{HTMLElement("input")}} است.

## مقدار

یک رشته که نوع را نشان می‌دهد.

مقادیر ممکن آن در بخش [انواع ورودی](/en-US/docs/Web/HTML/Reference/Elements/input#input_types) ویژگی ذکر شده است.

## مثال

### HTML

```html
<input id="input1" type="date" />
```

### JavaScript

```js
const inputElement = document.querySelector("#input1");
console.log(inputElement.type); // خروجی: "date"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- خاصیت {{domxref("HTMLTextAreaElement.type")}}
- خاصیت {{domxref("HTMLButtonElement.type")}}