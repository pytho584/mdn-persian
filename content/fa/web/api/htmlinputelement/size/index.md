---
title: "HTMLInputElement: size property"
short-title: size
slug: Web/API/HTMLInputElement/size
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.size
---

{{APIRef("HTML DOM")}}

خاصیت **`size`** در رابط {{DOMxRef("HTMLInputElement")}} تعداد کاراکترهای قابل مشاهده‌ای که نمایش داده می‌شود را مشخص می‌کند. این خاصیت منعکس‌کنندهٔ ویژگی [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) عنصر {{htmlelement("input")}} است.

خاصیت `size` فقط برای انواع ورودی [`text`](/en-US/docs/Web/HTML/Reference/Elements/input/text)، [`search`](/en-US/docs/Web/HTML/Reference/Elements/input/search)، [`tel`](/en-US/docs/Web/HTML/Reference/Elements/input/tel)، [`email`](/en-US/docs/Web/HTML/Reference/Elements/input/email)، [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url) و [`password`](/en-US/docs/Web/HTML/Reference/Elements/input/password) کاربرد دارد. مقدار آن یک عدد صحیح نامنفی بزرگ‌تر از صفر است. اگر حذف شود یا نامعتبر باشد، مقدار `20` در نظر گرفته می‌شود.

## مقدار

یک عدد صحیح.

## مثال‌ها

```js
const inputElement = document.getElementById("password");
console.log(inputElement.size);
inputElement.size = 12;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMXref("HTMLInputElement.minLength")}}
- {{DOMXref("HTMLInputElement.maxLength")}}
- {{DOMXref("HTMLSelectElement.size")}}