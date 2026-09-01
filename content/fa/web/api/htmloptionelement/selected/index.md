---
title: "HTMLOptionElement: selected property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLOptionElement/selected"
---

---
title: "HTMLOptionElement: selected property"
short-title: selected
slug: Web/API/HTMLOptionElement/selected
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.selected
---

{{ APIRef("HTML DOM") }}

ویژگی **`selected`** در رابط {{DOMxRef("HTMLOptionElement")}} وضعیت انتخاب‌شدگی فعلی عنصر را مشخص می‌کند؛ یعنی اینکه آیا {{HTMLElement("option")}} انتخاب شده است یا نه.

وجود ویژگی HTML [`selected`](/en-US/docs/Web/HTML/Reference/Elements/option#selected) نشان می‌دهد که گزینه به‌طور پیش‌فرض انتخاب شده است. اما این ویژگی نشان نمی‌دهد که آیا این گزینه در حال حاضر انتخاب شده است یا نه: اگر وضعیت گزینه تغییر کند، ویژگی محتوایی `selected` این تغییر را منعکس نمی‌کند؛ فقط ویژگی IDL به نام `selected` در `HTMLOptionElement` به‌روزرسانی می‌شود. ویژگی `selected` توسط ویژگی {{domxref("HTMLOptionElement.defaultSelected", "defaultSelected")}} بازتاب می‌شود.

## مقدار

یک مقدار بولی (boolean).

## مثال‌ها

```js
const optionElement = document.getElementById("water");
console.log(optionElement.selected);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("option")}}
- {{HTMLElement("select")}}
- {{DOMxRef("HTMLOptionElement.defaultSelected")}}
- {{DOMxRef("HTMLOptionElement.index")}}
- {{DOMxRef("HTMLOptionsCollection")}}
- {{DOMxRef("HTMLSelectElement.selectedIndex")}}