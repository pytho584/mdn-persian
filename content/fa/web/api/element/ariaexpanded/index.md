---
title: "Element: ariaExpanded property"
short-title: ariaExpanded
slug: Web/API/Element/ariaExpanded
page-type: web-api-instance-property
browser-compat: api.Element.ariaExpanded
---

{{APIRef("DOM")}}

ویژگی **`ariaExpanded`** در رابط {{domxref("Element")}}، مقدار ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) را بازتاب می‌دهد؛ این ویژگی نشان می‌دهد که آیا عنصر گروهی متعلق به این عنصر یا تحت کنترل آن، باز یا بسته است.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر گروهی که این عنصر مالک آن است یا آن را کنترل می‌کند، باز است.
- `"false"`
  - : عنصر گروهی که این عنصر مالک آن است یا آن را کنترل می‌کند، بسته است.
- `"undefined"`
  - : این عنصر، عنصر گروهی قابل باز و بسته شدن را در اختیار ندارد یا کنترل نمی‌کند.

## مثال‌ها

در این مثال، ویژگی `aria-expanded` روی عنصری با شناسه `animal` روی `"false"` تنظیم شده است. با استفاده از `ariaExpanded` مقدار آن را به `"true"` تغییر می‌دهیم.

```html
<div class="animals-combobox">
  <label for="animal">Animal</label>
  <input
    id="animal"
    type="text"
    role="combobox"
    aria-autocomplete="list"
    aria-expanded="false"
    aria-haspopup="true" />
  <button id="animals-button" tabindex="-1" aria-label="Open">▽</button>
  <ul id="animals-listbox" role="listbox" aria-label="Animals">
    <li id="animal-cat" role="option">Cat</li>
    <li id="animal-dog" role="option">Dog</li>
  </ul>
</div>
```

```js
let el = document.getElementById("animal");
console.log(el.ariaExpanded); // false
el.ariaExpanded = "true";
console.log(el.ariaExpanded); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}