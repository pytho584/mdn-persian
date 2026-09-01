---
title: "HTMLInputElement: disabled property"
short-title: disabled
slug: Web/API/HTMLInputElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.disabled
---

{{ APIRef("HTML DOM") }}

ویژگی **`HTMLInputElement.disabled`** یک مقدار بولی است که منعکس‌کنندهٔ ویژگی HTML [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/input#disabled) می‌باشد. این ویژگی مشخص می‌کند که آیا کنترل غیرفعال است یا خیر. اگر کنترل غیرفعال باشد، کلیک‌ها را نمی‌پذیرد. یک عنصر غیرفعال قابل استفاده و قابل کلیک نیست.

## مقدار

یک مقدار بولی.

## نمونه‌ها

### HTML

```html
<p>
  <label>
    <input id="check-box" name="b" value="1" type="checkbox" disabled /> Check
    this box!
  </label>
</p>
<p>
  <label>
    <input id="toggle-box" name="b" value="2" type="checkbox" /> Enable the
    other checkbox.
  </label>
</p>
```

### JavaScript

```js
const checkBox = document.getElementById("check-box");
const toggleBox = document.getElementById("toggle-box");

toggleBox.addEventListener("change", (event) => {
  checkBox.disabled = !event.target.checked;
});
```

### نتیجه

{{EmbedLiveSample('نمونه‌ها')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}