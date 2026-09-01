---
title: "Document: documentURI property"
short-title: documentURI
slug: Web/API/Document/documentURI
page-type: web-api-instance-property
browser-compat: api.Document.documentURI
---

{{ApiRef("DOM")}}

ویژگی فقط‌خواندنی **`documentURI`** در رابط {{domxref("Document")}}، مکان (آدرس) سند را به‌صورت یک رشته بازمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

### JavaScript

```js
document.getElementById("url").textContent = document.documentURI;
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

- ویژگی {{domxref("document.URL")}} که همان مقدار را بازمی‌گرداند.