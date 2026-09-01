```
---
title: "Document: documentElement property"
short-title: documentElement
slug: Web/API/Document/documentElement
page-type: web-api-instance-property
browser-compat: api.Document.documentElement
---

{{ApiRef("DOM")}}

خاصیت فقط‌خواندنی **`documentElement`** در رابط {{domxref("Document")}}، عنصر ریشه‌ی سند ({{domxref("document")}}) را برمی‌گرداند؛ برای مثال، عنصر {{HTMLElement("html")}} در اسناد HTML.

## مقدار

یک شیء {{domxref("Element")}}.

## مثال‌ها

```js
const rootElement = document.documentElement;
const firstTier = rootElement.childNodes;
// firstTier is a NodeList of the direct children of the root element
// such as <head> and <body>

for (const child of firstTier) {
  // do something with each direct child of the root element
}
```

## نکات

برای هر سند HTML غیرخالی، `documentElement` همیشه یک عنصر {{HTMLElement("html")}} خواهد بود. برای هر سند XML غیرخالی، `documentElement` همیشه همان عنصری خواهد بود که عنصر ریشه‌ی سند است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```