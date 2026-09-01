---
title: "DocumentType: remove() method"
short-title: remove()
slug: Web/API/DocumentType/remove
page-type: web-api-instance-method
browser-compat: api.DocumentType.remove
---

{{APIRef("DOM")}}

متد **`DocumentType.remove()`** مقدار `doctype` یک سند را حذف می‌کند.
اگر این `doctype` از قبل از سند جدا شده باشد، فراخوانی `remove()` هیچ اثری ندارد.

## سینتکس

```js-nolint
remove()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از `remove()`

```js
document.doctype; // "<!doctype html>'
document.doctype.remove();
document.doctype; // null
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Document.doctype")}}
- {{domxref("CharacterData.remove()")}}
- {{domxref("Element.remove()")}}