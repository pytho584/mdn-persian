---
title: "Document: scrollingElement property"
short-title: scrollingElement
slug: Web/API/Document/scrollingElement
page-type: web-api-instance-property
browser-compat: api.Document.scrollingElement
---

{{APIRef("DOM")}}

خاصیت فقط‌خواندنی **`scrollingElement`** در رابط {{domxref("Document")}} ارجاعی به عنصر {{domxref("Element")}} می‌دهد که سند را اسکرول می‌کند. در حالت استاندارد، این عنصر، عنصر ریشهٔ سند یعنی {{domxref("document.documentElement")}} است.

در حالت quirks، خاصیت `scrollingElement` عنصر `body` اچ‌تی‌ام‌ال را برمی‌گرداند، اگر وجود داشته باشد و [بالقوه قابل اسکرول](https://drafts.csswg.org/cssom-view/#potentially-scrollable) _نباشد_؛ در غیر این صورت مقدار `null` برمی‌گردد. این موضوع ممکن است شگفت‌آور به نظر برسد، اما طبق مشخصات و مرورگرها درست است.

## مقدار

عنصر {{domxref("Element")}} که سند را اسکرول می‌کند؛ معمولاً عنصر ریشه (مگر در حالتی که استاندارد نباشد).

## مثال‌ها

```js
const scrollElm = document.scrollingElement;
scrollElm.scrollTop = 0;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}