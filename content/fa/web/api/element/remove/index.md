---
title: "Element: remove() method"
short-title: remove()
slug: Web/API/Element/remove
page-type: web-api-instance-method
browser-compat: api.Element.remove
---

{{APIRef("DOM")}}

متد **`Element.remove()`** عنصر را از گرهٔ والد خود حذف می‌کند.
اگر عنصر گرهٔ والدی نداشته باشد، فراخوانی `remove()` هیچ کاری انجام نمی‌دهد.

## نحو

```js-nolint
remove()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از `remove()`

```html
<div id="div-01">Here is div-01</div>
<div id="div-02">Here is div-02</div>
<div id="div-03">Here is div-03</div>
```

```js
const element = document.getElementById("div-02");
element.remove(); // Removes the div with the 'div-02' id
```

### `Element.remove()` بدون دامنه است

متد `remove()` در محدودهٔ دستور `with` قرار نمی‌گیرد.
برای اطلاعات بیشتر به {{jsxref("Symbol.unscopables")}} مراجعه کنید.

```js
with (node) {
  remove();
}
// ReferenceError: remove is not defined
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.remove()")}}
- {{domxref("DocumentType.remove()")}}