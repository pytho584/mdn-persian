---
title: "Element: firstElementChild property"
short-title: firstElementChild
slug: Web/API/Element/firstElementChild
page-type: web-api-instance-property
browser-compat: api.Element.firstElementChild
---

{{ APIRef("DOM") }}

خاصیت فقط‌خواندنی **`Element.firstElementChild`** اولین عنصر فرزند ({{domxref("Element")}}) یک عنصر را برمی‌گرداند، یا اگر هیچ عنصر فرزندی وجود نداشته باشد، `null` را برمی‌گرداند.

`Element.firstElementChild` فقط گره‌های عنصر را شامل می‌شود. برای دریافت همهٔ گره‌های فرزند، از جمله گره‌های غیرعنصر مانند متن و کامنت، از {{domxref("Node.firstChild")}} استفاده کنید.

## مقدار

یک شیء {{domxref("Element")}}، یا `null`.

## مثال‌ها

```html
<ul id="list">
  <li>First (1)</li>
  <li>Second (2)</li>
  <li>Third (3)</li>
</ul>
```

```js
const list = document.getElementById("list");
console.log(list.firstElementChild.textContent);
// "First (1)" را در کنسول ثبت می‌کند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.nextElementSibling")}}
- {{domxref("Element.lastElementChild")}}