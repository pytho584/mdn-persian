---
title: "AbstractRange: collapsed property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/collapsed"
translated_by: "n8n + AI"
---

در رابط `AbstractRange`، ویژگی فقط‌خواندنی **`collapsed`** اگر موقعیت شروع و پایان محدوده یکی باشند، مقدار `true` را برمی‌گرداند.

یک محدودهٔ collapsed خالی است (هیچ محتوایی ندارد) و یک نقطهٔ واحد را در درخت DOM مشخص می‌کند. برای جمع کردن یک محدوده، به متد {{domxref("Range.collapse()")}} مراجعه کنید.

## مقدار

یک مقدار boolean که اگر محدوده _collapsed_ باشد `true` است. محدودهٔ collapsed به محدوده‌ای گفته می‌شود که موقعیت شروع و پایان آن یکی باشد و در نتیجه طول آن صفر کاراکتر است.

## مثال

```js
const range = document.createRange();
range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);

const isCollapsed = range.collapsed;
```