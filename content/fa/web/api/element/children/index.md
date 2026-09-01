---
title: "Element: children property"
short-title: children
slug: Web/API/Element/children
page-type: web-api-instance-property
browser-compat: api.Element.children
---

{{ APIRef("DOM") }}

ویژگی‌ی فقط‌خواندنی **`children`** یک {{domxref("HTMLCollection")}} زنده را بازمی‌گرداند که شامل تمام عناصر فرزند ({{domxref("Element", "elements")}}) عنصری است که روی آن فراخوانی شده است.

`Element.children` فقط گره‌های عنصر را شامل می‌شود. برای دریافت همه گره‌های فرزند، از جمله گره‌های غیرعنصری مانند گره‌های متنی و دیدگاه (comment)، از {{domxref("Node.childNodes")}} استفاده کنید.

## مقدار

یک {{ domxref("HTMLCollection") }} که مجموعه‌ای زنده و مرتب از عناصر DOM است که فرزندان `node` هستند. می‌توانید گره‌های فرزند جداگانه را در این مجموعه با استفاده از روش {{domxref("HTMLCollection.item()", "item()")}} یا با استفاده از نماد آرایه‌ای جاوااسکریپت دسترسی پیدا کنید.

اگر عنصر هیچ فرزند عنصری نداشته باشد، `children` یک فهرست خالی با `length` برابر با `0` است.

## مثال‌ها

```js
const myElement = document.getElementById("foo");
for (const child of myElement.children) {
  console.log(child.tagName);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.childNodes")}}