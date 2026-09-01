---
title: "HTMLAreaElement: toString() method"
short-title: toString()
slug: Web/API/HTMLAreaElement/toString
page-type: web-api-instance-method
browser-compat: api.HTMLAreaElement.toString
---

{{ApiRef("URL API")}}

متد **`HTMLAreaElement.toString()`** (رشته‌ساز) یک رشته شامل کل URL را برمی‌گرداند. این یک نسخهٔ فقط‌خواندنی از {{domxref("HTMLAreaElement.href")}} است.

## نحو (Syntax)

```js-nolint
toString()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک رشته شامل URL کامل عنصر.

## مثال‌ها

### فراخوانی toString روی یک عنصر area

```js
// یک عنصر <area id="myArea" href="/en-US/docs/HTMLAreaElement"> در سند وجود دارد
const area = document.getElementById("myArea");
area.toString(); // 'https://developer.mozilla.org/en-US/docs/HTMLAreaElement' را برمی‌گرداند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این متد به آن تعلق دارد.