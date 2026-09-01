---
title: "HTMLInputElement: alt property"
short-title: alt
slug: Web/API/HTMLInputElement/alt
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.alt
---

{{APIRef("HTML DOM")}}

خاصیت **`alt`** از اینترفیس {{DOMxRef("HTMLInputElement")}} برچسب متنی دکمه را برای کاربران و عامل‌های کاربری که نمی‌توانند از تصویر استفاده کنند تعریف می‌کند. این ویژگی منعکس‌کنندهٔ صفت [`alt`](/en-US/docs/Web/HTML/Reference/Elements/input#alt) در عنصر {{htmlelement("input")}} است.

خاصیت `alt` فقط برای نوع [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است. باید یک رشتهٔ غیرخالی باشد که برچسب مناسب برای یک دکمهٔ معادل در صورت عدم دسترسی به تصویر را ارائه دهد.

## مقدار

یک رشته (string).

## مثال‌ها

```js
const inputElement = document.getElementById("imageButton");
console.log(inputElement.alt);
inputElement.alt = "A much better description";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMXref("HTMLImageElement.alt")}}
- {{DOMXref("HTMLButtonElement")}}
- {{HTMLElement("button")}}
- {{HTMLElement("input")}}
- {{HTMLElement("img")}}
- [متن alt خوب، متن alt بد — قابل درک کردن محتوای خود](https://www.wcag.com/blog/good-alt-text-bad-alt-text-making-your-content-perceivable/) در WCAG.com (2021)
- [درخت تصمیم‌گیری برای alt](https://www.w3.org/WAI/tutorials/images/decision-tree/) در ابتکار دسترسی وب (WAI) کنسرسیوم وب جهان‌گستر (W3C)