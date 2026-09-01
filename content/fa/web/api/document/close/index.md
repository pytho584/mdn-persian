---
title: "Document: close() method"
---

---
title: "Document: close() method"
short-title: close()
slug: Web/API/Document/close
page-type: web-api-instance-method
browser-compat: api.Document.close
---

{{APIRef("DOM")}}

متد **`Document.close()`** نوشتن در سندی را که با {{domxref("Document.open()")}} باز شده است، به پایان می‌رساند.

## نحو

```js-nolint
close()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// Open a document to write to it
document.open();

// Write the content of the document
document.write("<p>The one and only content.</p>");

// Close the document
document.close();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}