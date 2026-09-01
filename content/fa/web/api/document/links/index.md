---
title: "Document: links property"
short-title: links
slug: Web/API/Document/links
page-type: web-api-instance-property
browser-compat: api.Document.links
---

{{ APIRef("DOM") }}

خاصیت فقط-خواندنی **`links`** در واسط {{domxref("Document")}} مجموعه‌ای از تمام عناصر {{HTMLElement("area")}} و {{HTMLElement("a")}} در سند را برمی‌گرداند که دارای مقدار برای ویژگی [href](/en-US/docs/Web/HTML/Reference/Elements/a#href) هستند.

## مقدار

یک {{domxref("HTMLCollection")}}.

## مثال‌ها

```js
for (const link of document.links) {
  const linkHref = document.createTextNode(link.href);
  const lineBreak = document.createElement("br");
  document.body.appendChild(linkHref);
  document.body.appendChild(lineBreak);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}