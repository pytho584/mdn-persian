---
title: "DocumentType: before() method"
short-title: before()
slug: Web/API/DocumentType/before
page-type: web-api-instance-method
browser-compat: api.DocumentType.before
---

{{APIRef("DOM")}}

متد **`DocumentType.before()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ `DocumentType`، دقیقاً قبل از خودِ `DocumentType` درج می‌کند. رشته‌ها به صورت گره‌های معادل {{domxref("Text")}} درج می‌شوند.

## نحو (Syntax)

```js-nolint
before(param1)
before(param1, param2)
before(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`، …، `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره نتواند در نقطه مشخص‌شده در سلسله‌مراتب درج شود.

## مثال‌ها

### افزودن یک کامنت شرطی

گره‌های کامنت قبل از اعلان‌های doctype معتبر هستند، اما توصیه نمی‌شوند، زیرا در IE حالت quirks را فعال می‌کنند. با این حال، یک [کامنت شرطی](https://www.sitepoint.com/internet-explorer-conditional-comments/) برای IE نیز کار می‌کند:

```js
let docType = document.implementation.createDocumentType("html", "", "");
let myDoc = document.implementation.createDocument("", "", docType);

docType.before(
  document.createComment("<!--[if !IE]> conditional comment <![endif]-->"),
);

myDoc.childNodes;
// NodeList [<!--[if !IE]> conditional comment <![endif]-->, <!DOCTYPE html>]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DocumentType.after()")}}
- {{domxref("CharacterData.before()")}}
- {{domxref("Element.before()")}}