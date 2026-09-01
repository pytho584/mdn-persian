---
title: "Document: replaceChildren() method"
short-title: replaceChildren()
slug: Web/API/Document/replaceChildren
page-type: web-api-instance-method
browser-compat: api.Document.replaceChildren
---

{{APIRef("DOM")}}

متد **`Document.replaceChildren()`** فرزندان موجود یک سند (`Document`) را با مجموعه‌ای مشخص از فرزندان جدید جایگزین می‌کند.

## سینتکس

```js-nolint
replaceChildren(param1)
replaceChildren(param1, param2)
replaceChildren(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`, …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای جایگزینی فرزندان موجود `Document`. اگر هیچ شیء جایگزینی مشخص نشود، تمام گره‌های فرزند از `Document` حذف می‌شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : اگر [محدودیت‌های درخت گره](https://dom.spec.whatwg.org/#concept-node-tree) نقض شوند، پرتاب می‌شود.

## مثال‌ها

### خالی کردن یک سند

`replaceChildren()` سازوکاری بسیار راحت برای خالی کردن یک سند از همه فرزندانش فراهم می‌کند. کافی است آن را بدون هیچ آرگومانی روی سند صدا بزنید:

```js
document.replaceChildren();
document.children; // HTMLCollection []
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.prepend()")}}
- {{domxref("Document.append()")}}