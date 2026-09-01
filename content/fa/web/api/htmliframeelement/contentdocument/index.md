---
title: "HTMLIFrameElement: contentDocument property"
short-title: contentDocument
slug: Web/API/HTMLIFrameElement/contentDocument
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.contentDocument
---

{{APIRef("HTML DOM")}}

اگر iframe و سندِ والدِ آن دارای [Same Origin](/en-US/docs/Web/Security/Defenses/Same-origin_policy) باشند، یک [`Document`](/en-US/docs/Web/API/Document) برمی‌گرداند (یعنی سندِ فعال در زمینهٔ مرورِ تودرتوی فریمِ درون‌خطی)؛ در غیر این صورت `null` برگردانده می‌شود.

## Example of contentDocument

```js
const iframeDocument = document.querySelector("iframe").contentDocument;

iframeDocument.body.style.backgroundColor = "blue";
// This would turn the iframe blue.
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}