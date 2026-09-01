```
---
title: "Document: prepend() method"
short-title: prepend()
slug: Web/API/Document/prepend
page-type: web-api-instance-method
browser-compat: api.Document.prepend
---

{{APIRef("DOM")}}

متد **`Document.prepend()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را قبل از اولین فرزند سند درج می‌کند. رشته‌ها به عنوان گره‌های {{domxref("Text")}} معادل درج می‌شوند.

این متد یک فرزند را به ابتدای یک `Document` اضافه می‌کند. برای prepend کردن به یک عنصر دلخواه در درخت، به {{domxref("Element.prepend()")}} مراجعه کنید.

## Syntax

```js-nolint
prepend(param1)
prepend(param1, param2)
prepend(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`, …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره در نقطه مشخص‌شده در سلسله‌مراتب قابل درج نباشد.

## مثال‌ها

### افزودن یک عنصر ریشه به ابتدای یک سند (prepend)

اگر تلاش کنید یک عنصر را به یک سند HTML موجود prepend کنید، ممکن است یک `HierarchyRequestError` {{domxref("DOMException")}} پرتاب شود زیرا یک عنصر {{HTMLElement("html")}} از قبل وجود دارد.

```js
let html = document.createElement("html");
document.prepend(html);
// HierarchyRequestError: The operation would yield an incorrect node tree.
```

اگر یک سند جدید بدون هیچ عنصر موجودی ایجاد می‌کنید، می‌توانید یک عنصر ریشه HTML (یا یک عنصر ریشه SVG) را prepend کنید:

```js
let doc = new Document();
let html = document.createElement("html");
doc.prepend(html);

doc.children; // HTMLCollection [<html>]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.append()")}}
- {{domxref("Element.prepend()")}}
```