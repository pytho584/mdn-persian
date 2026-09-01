---
title: "Element: lastElementChild property"
short-title: lastElementChild
slug: Web/API/Element/lastElementChild
page-type: web-api-instance-property
browser-compat: api.Element.lastElementChild
---

{{ APIRef("DOM") }}

خاصیت فقط‌خواندنی **`Element.lastElementChild`** آخرین فرزند {{domxref("Element")}} یک عنصر را برمی‌گرداند، یا در صورت نبود هیچ عنصر فرزندی، `null` را برمی‌گرداند.

`Element.lastElementChild` فقط گره‌های عنصر (element nodes) را شامل می‌شود. برای دریافت همه گره‌های فرزند، از جمله گره‌های غیرعنصر مانند متن و توضیحات، از {{domxref("Node.lastChild")}} استفاده کنید.

## مقدار

یک شیء {{domxref("Element")}}، یا `null`.

## مثال‌ها

```html
<ul id="list">
  <li>اول (1)</li>
  <li>دوم (2)</li>
  <li>سوم (3)</li>
</ul>
```

```js
const list = document.getElementById("list");
console.log(list.lastElementChild.textContent);
// چاپ می‌کند "سوم (3)"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.previousElementSibling")}}
- {{domxref("Element.firstElementChild")}}