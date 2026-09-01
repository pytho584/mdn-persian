---
title: "Element: ariaRowSpan property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/ariaRowSpan"
---

---
title: "Element: ariaRowSpan property"
short-title: ariaRowSpan
slug: Web/API/Element/ariaRowSpan
page-type: web-api-instance-property
browser-compat: api.Element.ariaRowSpan
---

{{APIRef("DOM")}}

ویژگی **`ariaRowSpan`** در رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan) است که تعداد ردیف‌های تحت پوشش یک سلول یا سلول شبکه‌ای را در یک جدول، شبکه یا درخت‌شبکه تعریف می‌کند.

## مقدار

رشته‌ای شامل یک عدد صحیح.

## مثال‌ها

در این مثال، ویژگی `aria-rowspan` روی عنصری با شناسهٔ `spanning-heading` برابر «۳» تنظیم شده است. با استفاده از `ariaRowSpan` مقدار را به «۲» تغییر می‌دهیم.

```html
<table>
  <thead>
    <tr>
      <th id="spanning-heading" rowspan="3" aria-rowspan="3">
        Spanning heading
      </th>
      <th>Heading</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>One</td>
    </tr>
    <tr>
      <td>Two</td>
    </tr>
  </tbody>
</table>
```

```js
let el = document.getElementById("spanning-heading");
console.log(el.ariaRowSpan);
el.ariaRowSpan = "2";
console.log(el.ariaRowSpan);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)