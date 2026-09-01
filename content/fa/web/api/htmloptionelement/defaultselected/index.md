---
title: "HTMLOptionElement: defaultSelected property"
short-title: defaultSelected
slug: Web/API/HTMLOptionElement/defaultSelected
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.defaultSelected
---

{{ APIRef("HTML DOM") }}

خاصیت **`defaultSelected`** از رابط {{DOMxRef("HTMLOptionElement")}} وضعیت انتخاب‌شده پیش‌فرض عنصر را مشخص می‌کند. این خاصیت منعکس‌کنندهٔ ویژگی [`selected`](/en-US/docs/Web/HTML/Reference/Elements/option#selected) عنصر {{htmlelement("option")}} است. وجود ویژگی `selected`، خاصیت `defaultSelected` را به `true` تنظیم می‌کند.

## مقدار

یک مقدار بولی (Boolean).

## مثال‌ها

```js
const optionElement = document.getElementById("water");
console.log(optionElement.defaultSelected);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("option")}}
- {{DOMxRef("HTMLOptionElement.selected")}}
- {{DOMxRef("HTMLOptionElement.index")}}
- {{DOMxRef("HTMLOptionsCollection")}}
- {{cssxref(":default")}}