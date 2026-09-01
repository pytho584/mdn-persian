---
title: "DocumentType: after() method"
short-title: after()
slug: Web/API/DocumentType/after
page-type: web-api-instance-method
browser-compat: api.DocumentType.after
---

{{APIRef("DOM")}}

متد **`DocumentType.after()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در لیست فرزندان والد `DocumentType`، درست بعد از `DocumentType` درج می‌کند. رشته‌ها به عنوان گره‌های {{domxref("Text")}} معادل درج می‌شوند.

## نحو

```js-nolint
after(param1)
after(param1, param2)
after(param1, param2, /* …, */ paramN)
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

```js
let docType = document.implementation.createDocumentType("html", "", "");
let myDoc = document.implementation.createDocument("", "", docType);

docType.after(document.createElement("html"));

myDoc.childNodes;
// NodeList [<!DOCTYPE html>, <html>]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DocumentType.before()")}}
- {{domxref("CharacterData.after()")}}
- {{domxref("Element.after()")}}