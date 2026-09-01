---
title: "Element: ariaChecked property"
short-title: ariaChecked
slug: Web/API/Element/ariaChecked
page-type: web-api-instance-property
browser-compat: api.Element.ariaChecked
---

{{APIRef("DOM")}}

ویژگی **`ariaChecked`** از رابط {{domxref("Element")}} منعکس‌کننده مقدار ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) است که وضعیت «تیک‌خورده» فعلی چک‌باکس‌ها، دکمه‌های رادیویی و سایر ابزارک‌هایی که حالت تیک‌خورده دارند را نشان می‌دهد.

> [!NOTE]
> در صورت امکان، از عنصر HTML {{htmlelement("input")}} با `type="checkbox"` استفاده کنید، زیرا این عنصر معناشناسی داخلی دارد و به ویژگی‌های ARIA نیازی ندارد.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر تیک خورده است.
- `"mixed"`
  - : حالت ترکیبی را برای یک چک‌باکس یا منوی آیتم‌چک‌باکس سه‌حالته نشان می‌دهد.
- `"false"`
  - : عنصر از تیک‌خوردن پشتیبانی می‌کند اما در حال حاضر تیک نخورده است.
- `"undefined"`
  - : عنصر از تیک‌خوردن پشتیبانی نمی‌کند.

## مثال‌ها

در این مثال، ویژگی `aria-checked` روی عنصری با شناسه `checkBoxInput` روی «false» تنظیم شده است که نشان می‌دهد این ورودی در حال حاضر تیک نخورده است. با استفاده از `ariaChecked` مقدار آن را به «true» به‌روزرسانی می‌کنیم.

```html
<span
  role="checkbox"
  id="checkBoxInput"
  aria-checked="false"
  tabindex="0"
  aria-labelledby="chk1-label">
</span>
<label id="chk1-label">Remember my preferences</label>
```

```js
let el = document.getElementById("checkBoxInput");
console.log(el.ariaChecked); // "false"
el.ariaChecked = "true";
console.log(el.ariaChecked); // "true"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش checkbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)