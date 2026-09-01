---
title: "HTMLSelectElement: remove() method"
short-title: remove()
slug: Web/API/HTMLSelectElement/remove
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.remove
---

{{ APIRef("HTML DOM") }}

متد **`HTMLSelectElement.remove()`** عنصر موجود در اندیس مشخص‌شده را از مجموعه‌ی گزینه‌های این عنصر select حذف می‌کند.

## نحو (Syntax)

```js-nolint
remove(index)
```

### پارامترها

- `index`
  - : یک عدد صحیح مبتنی بر صفر برای اندیس {{ domxref("HTMLOptionElement") }} که باید از مجموعه حذف شود. اگر اندیس یافت نشود، متد هیچ اثری ندارد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```html
<select id="existingList" name="existingList">
  <option value="1">Option: Value 1</option>
  <option value="2">Option: Value 2</option>
  <option value="3">Option: Value 3</option>
</select>
```

```js
let sel = document.getElementById("existingList");
sel.remove(1);
```

HTML اکنون به این صورت است:

```html
<select id="existingList" name="existingList">
  <option value="1">Option: Value 1</option>
  <option value="3">Option: Value 3</option>
</select>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("Element.remove") }}، متدی که وقتی `remove` بدون آرگومان روی یک {{ domxref("HTMLSelectElement") }} فراخوانی می‌شود، صدا زده می‌شود.
- {{domxref("HTMLSelectElement") }} که آن را پیاده‌سازی می‌کند.