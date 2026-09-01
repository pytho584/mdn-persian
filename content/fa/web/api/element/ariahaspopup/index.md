---
title: "Element: ariaHasPopup property"
short-title: ariaHasPopup
slug: Web/API/Element/ariaHasPopup
page-type: web-api-instance-property
browser-compat: api.Element.ariaHasPopup
---

{{APIRef("DOM")}}

ویژگی **`ariaHasPopup`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار صفت [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) است که در دسترس بودن و نوع عنصر پاپ‌آپ تعاملی، مانند منو یا دیالوگ، که می‌تواند توسط یک عنصر فعال شود را نشان می‌دهد.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"false"` - عنصر پاپ‌آپ ندارد.
- `"true"` - عنصر دارای پاپ‌آپی از نوع منو است.
- `"menu"` - عنصر دارای پاپ‌آپی از نوع منو است.
- `"listbox"` - عنصر دارای پاپ‌آپی از نوع لیست‌باکس است.
- `"tree"` - عنصر دارای پاپ‌آپی از نوع درخت است.
- `"grid"` - عنصر دارای پاپ‌آپی از نوع شبکه است.
- `"dialog"` - عنصر دارای پاپ‌آپی از نوع دیالوگ است.

> [!WARNING]
> توجه داشته باشید که پشتیبانی از مقادیر مختلف `aria-haspopup` بسته به عنصری که صفت به آن اختصاص داده شده است می‌تواند متفاوت باشد. اطمینان حاصل کنید که هنگام استفاده از `aria-haspopup`، این کار مطابق با مشخصات ARIA انجام شود و در آزمایش با مرورگرها و فناوری‌های کمکی لازم، رفتار مورد انتظار را داشته باشد.

## مثال‌ها

در این مثال، صفت `aria-haspopup` روی عنصری با شناسهٔ `animal` به مقدار `"true"` تنظیم شده است. با استفاده از `ariaHasPopup`، مقدار را به `"listbox"` به‌روزرسانی می‌کنیم که مقدار مورد انتظار برای یک جعبه‌ترکیبی (combobox) است که یک پاپ‌آپ از نوع لیست‌باکس را فراخوانی می‌کند.

```html
<div class="animals-combobox">
  <label for="animal">Animal</label>
  <input
    id="animal"
    type="text"
    role="combobox"
    aria-autocomplete="list"
    aria-controls="animals-listbox"
    aria-activedescendant=""
    aria-expanded="false"
    aria-haspopup="true" />
  <ul id="animals-listbox" role="listbox" aria-label="Animals">
    <li id="animal-cat" role="option">Cat</li>
    <li id="animal-dog" role="option">Dog</li>
  </ul>
</div>
```

```js
let el = document.getElementById("animal");
console.log(el.ariaHasPopup); // true
el.ariaHasPopup = "listbox";
console.log(el.ariaHasPopup); // listbox
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}