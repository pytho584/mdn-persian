---
title: "HTMLSelectElement: item() method"
short-title: item()
slug: Web/API/HTMLSelectElement/item
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.item
---

{{ APIRef("HTML DOM") }}

متد **`HTMLSelectElement.item()`** عنصر {{domxref("Element")}} متناظر با {{domxref("HTMLOptionElement")}} را برمی‌گرداند که موقعیت آن در فهرست گزینه‌ها با اندیس داده‌شده در پارامتر مطابقت دارد؛ اگر چنین گزینه‌ای وجود نداشته باشد، `null` برگردانده می‌شود.

در جاوااسکریپت، استفاده از نحو براکت‌گذاری آرایه‌ای با یک عدد صحیح بدون علامت، مانند `selectElt[index]`، معادل `selectElt.item(index)` است.

## Syntax

```js-nolint
item(index)
// or collection[index]
```

### Parameters

- `index`
  - : یک عدد صحیح نامنفی که موقعیت گزینه را در فهرست نشان می‌دهد.

### Return value

یک {{domxref("HTMLOptionElement")}} یا `null`.

## Examples

### HTML

```html
<form>
  <select id="myFormControl">
    <option id="o1">Opt 1</option>
    <option id="o2">Opt 2</option>
  </select>
</form>
```

### JavaScript

```js
// Returns the HTMLOptionElement representing #o2
elem1 = document.forms[0]["myFormControl"][1];
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLSelectElement")}} که آن را پیاده‌سازی می‌کند.
