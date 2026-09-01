---
title: "Element: ariaMultiSelectable property"
---

---
title: "Element: ariaMultiSelectable property"
short-title: ariaMultiSelectable
slug: Web/API/Element/ariaMultiSelectable
page-type: web-api-instance-property
browser-compat: api.Element.ariaMultiSelectable
---

{{APIRef("DOM")}}

خاصیت **`ariaMultiSelectable`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-multiselectable`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable) را منعکس می‌کند. این ویژگی نشان می‌دهد که کاربر می‌تواند بیش از یک مورد را از میان فرزندان قابل‌انتخاب فعلی انتخاب کند.

> [!NOTE]
> در صورت امکان، از عنصر HTML {{htmlelement("select")}} استفاده کنید، زیرا این عنصر معنای توکار دارد و به ویژگی‌های ARIA نیازی ندارد.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - بیش از یک مورد می‌تواند همزمان انتخاب شود.
- `"false"`
  - فقط یک مورد می‌تواند انتخاب شود.

## نمونه‌ها

در این مثال، ویژگی `aria-multiselectable` روی عنصری با شناسه `listbox1` به «true» تنظیم شده است که نشان می‌دهد این عنصر انتخاب‌شونده‌های چندتایی را می‌پذیرد. با استفاده از `ariaMultiSelectable` مقدار آن را به «false» تغییر می‌دهیم.

```html
<div
  role="listbox"
  tabindex="0"
  id="listbox1"
  aria-multiselectable="true"
  aria-labelledby="listbox1label"
  aria-activedescendant="listbox1-1">
  <div role="option" id="listbox1-1" class="selected" aria-selected="true">
    Green
  </div>
  <div role="option" id="listbox1-2">Orange</div>
  <div role="option" id="listbox1-3">Red</div>
</div>
```

```js
let el = document.getElementById("listbox1");
console.log(el.ariaMultiSelectable); // "true"
el.ariaMultiSelectable = "false";
console.log(el.ariaMultiSelectable); // "false"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش ARIA: listbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)