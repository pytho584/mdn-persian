---
title: "Document: rootElement property"
short-title: rootElement
slug: Web/API/Document/rootElement
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.rootElement
---

{{ApiRef("DOM")}}{{Deprecated_header}}

ویژگی **`Document.rootElement`**، عنصر ریشه ({{domxref("Element")}}) سند ({{domxref("document")}}) را برمی‌گرداند، اگر آن عنصر یک عنصر {{SVGElement("svg")}} باشد؛ در غیر این صورت `null` برمی‌گرداند. این ویژگی به نفع {{domxref("Document.documentElement")}} منسوخ (deprecated) شده است که عنصر ریشه را برای تمام اسناد برمی‌گرداند.

## مقدار

برای عناصر SVG، {{domxref("Element")}} ریشه سند {{domxref("document")}}؛ در غیر این صورت `null`.

اگر سند یک سند SVG غیر خالی باشد، `rootElement` یک {{domxref("SVGSVGElement")}} خواهد بود که مشابه `documentElement` است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}