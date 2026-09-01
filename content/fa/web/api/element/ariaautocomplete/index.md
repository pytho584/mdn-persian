---
title: "Element: ariaAutoComplete property"
---

---
title: "Element: ariaAutoComplete property"
short-title: ariaAutoComplete
slug: Web/API/Element/ariaAutoComplete
page-type: web-api-instance-property
browser-compat: api.Element.ariaAutoComplete
---

{{APIRef("DOM")}}

ویژگی **`ariaAutoComplete`** در رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete) است؛ این ویژگی نشان می‌دهد که آیا وارد کردن متن می‌تواند نمایش یک یا چند پیش‌بینی از مقدار موردنظر کاربر را برای combobox، searchbox یا textbox فعال کند و همچنین مشخص می‌کند که پیش‌بینی‌ها در صورت ارائه چگونه نمایش داده شوند.

## Value

یک رشته با یکی از مقادیر زیر:

- `"inline"`
  - : وقتی کاربر در حال وارد کردن ورودی است، متنی که راهی برای تکمیل ورودی ارائه‌شده پیشنهاد می‌کند، ممکن است به‌صورت پویا پس از مکان‌نما درج شود.
- `"list"`
  - : وقتی کاربر در حال وارد کردن ورودی است، ممکن است عنصری حاوی مجموعه‌ای از مقادیر که می‌توانند ورودی ارائه‌شده را تکمیل کنند، نمایش داده شود.
- `"both"`
  - : وقتی کاربر در حال وارد کردن ورودی است، ممکن است عنصری حاوی مجموعه‌ای از مقادیر که می‌توانند ورودی ارائه‌شده را تکمیل کنند، نمایش داده شود. در صورت نمایش، یکی از مقادیر موجود در مجموعه به‌صورت خودکار انتخاب می‌شود و متن لازم برای تکمیل مقدار انتخاب‌شده‌به‌صورت‌خودکار، پس از مکان‌نما در ورودی ظاهر می‌شود.
- `"none"`
  - : وقتی کاربر در حال وارد کردن ورودی است، هیچ پیشنهاد خودکاری برای پیش‌بینی نحوهٔ تکمیل ورودی توسط کاربر نمایش داده نمی‌شود.

## Examples

در این مثال، ویژگی `aria-autocomplete` روی عنصری با شناسهٔ `animal` روی مقدار `"inline"` تنظیم شده است. با استفاده از `ariaAutoComplete` مقدار را به `"list"` تغییر می‌دهیم؛ این مقدار مورد انتظار برای یک combobox است که یک popup از نوع `listbox` را فراخوانی می‌کند.

```html
<div class="animals-combobox">
  <label for="animal">Animal</label>
  <input
    id="animal"
    type="text"
    role="combobox"
    aria-autocomplete="inline"
    aria-controls="animals-listbox"
    aria-expanded="false"
    aria-haspopup="listbox" />
  <ul id="animals-listbox" role="listbox" aria-label="Animals">
    <li id="animal-cat" role="option">Cat</li>
    <li id="animal-dog" role="option">Dog</li>
  </ul>
</div>
```

```js
let el = document.getElementById("animal");
console.log(el.ariaAutoComplete); // inline
el.ariaAutoComplete = "list";
console.log(el.ariaAutoComplete); // list
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}