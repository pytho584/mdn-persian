---
title: "Document: append() method"
short-title: append()
slug: Web/API/Document/append
page-type: web-api-instance-method
browser-compat: api.Document.append
---

{{APIRef("DOM")}}

متد **`Document.append()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را بعد از آخرین فرزند سند درج می‌کند. رشته‌ها به‌صورت گره‌های {{domxref("Text")}} معادل درج می‌شوند.

این متد یک فرزند به `Document` اضافه می‌کند. برای افزودن به یک عنصر دلخواه در درخت، به {{domxref("Element.append()")}} مراجعه کنید.

## Syntax

```js-nolint
append(param1)
append(param1, param2)
append(param1, param2, /* …, */ paramN)
```

### Parameters

- `param1`, …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره نتواند در نقطه مشخص‌شده در سلسله‌مراتب درج شود.

## Examples

### افزودن یک عنصر ریشه به سند

اگر بخواهید یک عنصر به یک سند HTML موجود اضافه کنید، ممکن است با توجه به وجود عنصر {{HTMLElement("html")}}، خطای `HierarchyRequestError` {{domxref("DOMException")}} پرتاب شود.

```js
let html = document.createElement("html");
document.append(html);
// HierarchyRequestError: The operation would yield an incorrect node tree.
```

اگر در حال ایجاد یک سند جدید بدون هیچ عنصر موجودی هستید، می‌توانید یک عنصر ریشه HTML (یا یک عنصر ریشه SVG) اضافه کنید:

```js
let doc = new Document();
let html = document.createElement("html");
doc.append(html);

doc.children; // HTMLCollection [<html>]
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.prepend()")}}
- {{domxref("Element.append()")}}