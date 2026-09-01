```
---
title: "HTMLSelectElement: namedItem() method"
---

---
title: "HTMLSelectElement: namedItem() method"
short-title: namedItem()
slug: Web/API/HTMLSelectElement/namedItem
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.namedItem
---

{{ APIRef("HTML DOM") }}

متد **`HTMLSelectElement.namedItem()`**، {{domxref("HTMLOptionElement")}} مربوط به گزینه‌ای را برمی‌گرداند که `name` یا `id` آن با نام مشخص‌شده مطابقت دارد؛ اگر هیچ گزینه‌ای مطابقت نداشته باشد، `null` برمی‌گرداند.

در جاوااسکریپت، استفاده از `selectElt.namedItem('value')` معادل `selectElt.options.namedItem('value')` است.

## سینتکس

```js-nolint
namedItem(str)
```

### پارامترها

- `str`
  - : یک رشته که نمایانگر `name` یا `id` گزینه است.

### مقدار بازگشتی

یک {{domxref("HTMLOptionElement")}} یا `null` است.

## مثال‌ها

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
let selectElt = document.getElementById("myFormControl");
elem1 = selectElt.namedItem("o1"); // Returns the HTMLOptionElement representing #o1
```

اما نمی‌توانید بنویسید:

```js
let selectElt = document.getElementById("myFormControl");
elem1 = selectElt.o1; // Returns undefined
elem1 = selectElt["o1"]; // Returns undefined
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLSelectElement")}} که آن را پیاده‌سازی می‌کند.
```