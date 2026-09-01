---
title: "Element: slot property"
short-title: slot
slug: Web/API/Element/slot
page-type: web-api-instance-property
browser-compat: api.Element.slot
---

{{APIRef("Shadow DOM")}}

ویژگی **`slot`** در رابط {{domxref("Element")}} نام اسلاتِ DOM سایه‌ای را برمی‌گرداند که عنصر در آن قرار گرفته است.

اسلات یک مکان نگهدارنده در داخل یک [کامپوننت وب](/en-US/docs/Web/API/Web_components) است که کاربران می‌توانند آن را با نشانه‌گذاری خودشان پر کنند (برای اطلاعات بیشتر به [استفاده از تمپلیت‌ها و اسلات‌ها](/en-US/docs/Web/API/Web_components/Using_templates_and_slots) مراجعه کنید).

## مقدار

یک رشته (string).

## مثال‌ها

در [مثال simple-template](https://github.com/mdn/web-components-examples/tree/main/simple-template) ما ([مشاهده آنلاین](https://mdn.github.io/web-components-examples/simple-template/))، یک نمونه عنصر سفارشی ساده به نام `<my-paragraph>` می‌سازیم که در آن یک ریشه سایه (shadow root) متصل شده و سپس با محتویات یک تمپلیت که شامل اسلاتی به نام `my-text` است پر می‌شود.

هنگامی که `<my-paragraph>` در سند استفاده می‌شود، اسلات توسط یک عنصر قابل‌اسلات (slottable) پر می‌شود؛ به این صورت که آن عنصر را با ویژگی [`slot`](/en-US/docs/Web/HTML/Reference/Global_attributes/slot) به مقدار `my-text` داخل عنصر قرار می‌دهیم. در اینجا یک نمونه از این کار آمده است:

```html
<my-paragraph>
  <span slot="my-text">Let's have some different text!</span>
</my-paragraph>
```

در فایل جاوااسکریپت خود، به عنصر {{htmlelement("span")}} نمایش داده شده در بالا ارجاع می‌گیریم و سپس نام عنصر `<slot>` مربوطه را در خروجی ثبت می‌کنیم.

```js
let slottedSpan = document.querySelector("my-paragraph span");
console.log(slottedSpan.slot); // 'my-text' را ثبت می‌کند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}