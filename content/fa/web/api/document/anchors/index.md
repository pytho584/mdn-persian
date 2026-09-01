---
title: "Document: anchors property"
short-title: anchors
slug: Web/API/Document/anchors
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.anchors
---

{{APIRef("DOM")}} {{Deprecated_Header}}

ویژگی فقط‌خواندنی **`anchors`** در رابط {{domxref("Document")}} فهرستی از تمام لنگرگاه‌های (Anchor) سند را برمی‌گرداند.

## مقدار

یک {{domxref("HTMLCollection")}}.

## مثال‌ها

### استفادهٔ پایه

```js
if (document.anchors.length >= 5) {
  console.log("found too many anchors");
}
```

### ایجاد فهرست مطالب

مثال زیر فهرست مطالب را به‌صورت خودکار با تمام لنگرگاه‌های صفحه پر می‌کند:

```html
<h1>Title</h1>
<h2><a name="contents">Contents</a></h2>
<ul id="toc"></ul>

<h2><a name="plants">Plants</a></h2>
<ol>
  <li>Apples</li>
  <li>Oranges</li>
  <li>Pears</li>
</ol>

<h2><a name="veggies">Veggies</a></h2>
<ol>
  <li>Carrots</li>
  <li>Celery</li>
  <li>Beats</li>
</ol>
```

```js
const toc = document.getElementById("toc");
for (const anchor of document.anchors) {
  const li = document.createElement("li");
  const newAnchor = document.createElement("a");
  newAnchor.href = `#${anchor.name}`;
  newAnchor.textContent = anchor.text;
  li.appendChild(newAnchor);
  toc.appendChild(li);
}
```

{{EmbedLiveSample("Creating a table of contents", "", 500)}}

## نکات

به دلایل سازگاری با نسخه‌های قبلی، مجموعهٔ بازگردانده‌شده از لنگرگاه‌ها فقط آنهایی را شامل می‌شود که با ویژگی `name` ساخته شده‌اند، نه آنهایی که با ویژگی `id` ساخته شده‌اند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}