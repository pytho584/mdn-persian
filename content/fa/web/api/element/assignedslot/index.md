---
title: "Element: assignedSlot property"
short-title: assignedSlot
slug: Web/API/Element/assignedSlot
page-type: web-api-instance-property
browser-compat: api.Element.assignedSlot
---

{{APIRef("Shadow DOM")}}

خاصیت فقط‌خواندنی **`assignedSlot`** در رابط {{domxref("Element")}} یک {{domxref("HTMLSlotElement")}} برمی‌گرداند که نشان‌دهندهٔ عنصر {{htmlelement("slot")}} است که گره در آن درج شده است.

## مقدار

یک نمونه از {{domxref('HTMLSlotElement')}}، یا `null` اگر عنصر به هیچ اسلاتی اختصاص داده نشده باشد، یا اگر ریشهٔ سایه‌ای مرتبط با ویژگی {{domxref("ShadowRoot.mode", "mode")}} آن روی `closed` تنظیم شده باشد (برای جزئیات بیشتر به {{domxref("Element.attachShadow")}} مراجعه کنید).

## مثال‌ها

در [مثال قالب ساده](https://github.com/mdn/web-components-examples/tree/main/simple-template) ما ([مشاهده زنده](https://mdn.github.io/web-components-examples/simple-template/))، یک مثال عنصر سفارشی ساده به نام `<my-paragraph>` ایجاد می‌کنیم که در آن یک ریشهٔ سایه‌ای متصل شده و سپس با استفاده از محتویات یک قالب که شامل یک اسلات به نام `my-text` است پر می‌شود.

هنگامی که `<my-paragraph>` در سند استفاده می‌شود، اسلات توسط یک عنصر قابل‌اسلات‌گذاری پر می‌شود که آن را در داخل عنصر با یک ویژگی [`slot`](/en-US/docs/Web/HTML/Reference/Global_attributes/slot) با مقدار `my-text` قرار می‌دهیم. در اینجا یک نمونه از این چنین است:

```html
<my-paragraph>
  <span slot="my-text">Let's have some different text!</span>
</my-paragraph>
```

در فایل جاوااسکریپت خود، به عنصر {{htmlelement("span")}} نشان‌داده‌شده در بالا ارجاع می‌گیریم و سپس ارجاعی به عنصر اصلی `<slot>` که `<span>` در آن درج شده بود را ثبت می‌کنیم.

```js
let slottedSpan = document.querySelector("my-paragraph span");
console.log(slottedSpan.assignedSlot); // logs '<slot name="my-text">'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}