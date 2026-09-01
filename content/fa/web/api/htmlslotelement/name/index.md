---
title: "HTMLSlotElement: name property"
short-title: name
slug: Web/API/HTMLSlotElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLSlotElement.name
---

{{APIRef("Shadow DOM API")}}

ویژگی **`name`** در رابط {{domxref("HTMLSlotElement")}}، نام اسلات را برمی‌گرداند یا تنظیم می‌کند. اسلات یک جایگاه خالی در یک کامپوننت وب است که کاربران می‌توانند آن را با نشانه‌گذاری (مارک‌آپ) خودشان پر کنند.

## مقدار

یک رشته (string).

## نمونه‌ها

قطعه کد زیر از مثال [تغییر اسلات (slotchange)](https://github.com/mdn/web-components-examples/tree/main/slotchange) گرفته شده است ([نمایش زنده](https://mdn.github.io/web-components-examples/slotchange/)).

```js
let slots = this.shadowRoot.querySelectorAll("slot");
slots[1].addEventListener("slotchange", (e) => {
  let nodes = slots[1].assignedNodes();
  console.log(
    `Element in Slot "${slots[1].name}" changed to "${nodes[0].outerHTML}".`,
  );
});
```

در اینجا، ارجاع‌هایی به همه اسلات‌ها می‌گیریم و سپس یک شنونده رویداد `slotchange` به دومین اسلات در قالب اضافه می‌کنیم — همان اسلاتی که در مثال محتوایش مدام تغییر می‌کند.

هر بار که عنصر درون اسلات تغییر می‌کند، گزارشی را در کنسول ثبت می‌کنیم که نشان می‌دهد کدام اسلات تغییر کرده و گره جدید داخل اسلات چیست.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}