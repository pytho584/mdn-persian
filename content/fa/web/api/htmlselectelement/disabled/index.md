---
title: "HTMLSelectElement: disabled property"
short-title: disabled
slug: Web/API/HTMLSelectElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.disabled
---

{{ APIRef("HTML DOM") }}

ویژگی **`HTMLSelectElement.disabled`** یک مقدار بولی (boolean) است که ویژگی HTML
[`disabled`](/en-US/docs/Web/HTML/Reference/Elements/select#disabled)
را منعکس می‌کند. این ویژگی نشان می‌دهد که آیا کنترل غیرفعال است یا خیر. اگر غیرفعال باشد، کلیک‌ها را نمی‌پذیرد. یک عنصر غیرفعال قابل استفاده و کلیک نیست.

## مقدار

یک مقدار بولی.

## مثال‌ها

### HTML

```html
<label>
  اجازه نوشیدنی؟
  <input id="allow-drinks" type="checkbox" />
</label>

<label for="drink-select">انتخاب نوشیدنی:</label>
<select id="drink-select" disabled>
  <option value="1">آب</option>
  <option value="2">آبجو</option>
  <option value="3">پپسی</option>
  <option value="4">ویسکی</option>
</select>
```

### JavaScript

```js
const allowDrinksCheckbox = document.getElementById("allow-drinks");
const drinkSelect = document.getElementById("drink-select");

allowDrinksCheckbox.addEventListener("change", (event) => {
  drinkSelect.disabled = !event.target.checked;
});
```

### نتیجه

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}