---
title: "Element: classList property"
short-title: classList
slug: Web/API/Element/classList
page-type: web-api-instance-property
browser-compat: api.Element.classList
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`classList`** در رابط {{domxref("Element")}} شامل یک مجموعهٔ زندهٔ {{domxref("DOMTokenList")}} است که صفت `class` عنصر را نمایش می‌دهد. سپس می‌توان از این مجموعه برای دستکاری فهرست کلاس‌ها استفاده کرد.

استفاده از `classList` جایگزین مناسبی برای دسترسی به فهرست کلاس‌های یک عنصر به‌صورت رشته‌ای جدا شده با فاصله از طریق {{domxref("element.className")}} است.

## مقدار

یک شیء {{domxref("DOMTokenList")}} که محتوای صفت `class` عنصر را نشان می‌دهد. اگر صفت `class` تنظیم نشده باشد یا خالی باشد، یک `DOMTokenList` خالی برمی‌گرداند؛ یعنی یک `DOMTokenList` که ویژگی `length` آن برابر با `0` است.

اگرچه خود ویژگی `classList` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به `classList` مقدار اختصاص دهید که معادل اختصاص دادن به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```js
const div = document.createElement("div");
div.classList = "foo"; // forwarded to classList.value

// our starting state: <div class="foo"></div>
console.log(div.outerHTML);

// use the classList API to remove and add classes
div.classList.remove("foo");
div.classList.add("another-class");

// <div class="another-class"></div>
console.log(div.outerHTML);

// if visible is set remove it, otherwise add it
div.classList.toggle("visible");

// add/remove visible, depending on test conditional, i less than 10
div.classList.toggle("visible", i < 10);

// false
console.log(div.classList.contains("foo"));

// add or remove multiple classes
div.classList.add("foo", "bar", "baz");
div.classList.remove("foo", "bar", "baz");

// add or remove multiple classes using spread syntax
const cls = ["foo", "bar"];
div.classList.add(...cls);
div.classList.remove(...cls);

// replace class "foo" with class "bar"
div.classList.replace("foo", "bar");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.className")}}
- {{domxref("DOMTokenList")}}