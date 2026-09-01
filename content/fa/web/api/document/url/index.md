---
title: "Document: URL property"
short-title: URL
slug: Web/API/Document/URL
page-type: web-api-instance-property
browser-compat: api.Document.URL
---

{{APIRef("DOM")}}

خاصیت فقط‌خواندنی **`URL`** در رابط {{domxref("Document")}}، آدرس (location) سند را به صورت یک رشته بازمی‌گرداند.

## مقدار

رشته‌ای شامل URL سند.

## مثال‌ها

### جاوااسکریپت

```js
document.getElementById("url").textContent = document.URL;
```

### HTML

```html
<p id="urlText">
  URL:<br />
  <span id="url">URL goes here</span>
</p>
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- خاصیت {{domxref("document.documentURI")}} که همان مقدار را بازمی‌گرداند.