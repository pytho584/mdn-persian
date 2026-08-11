---
title: "AbstractRange: endContainer property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/endContainer"
translated_by: "n8n + AI"
---

ویژگی فقط‌خواندنی **`endContainer`** در واسط {{domxref("AbstractRange")}}، {{domxref("Node")}}‌ای را که انتهای محدوده (range) در آن قرار دارد برمی‌گرداند.

برای تغییر موقعیت انتهایی محدوده، از متد {{domxref("Range.setEnd()")}} یا متدی مشابه استفاده کنید.

## مقدار

{{domxref("Node")}}‌ای که آخرین کاراکتر محدوده را در خود دارد.

## مثال

```js
const range = document.createRange();
range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);

const endRangeNode = range.endContainer;
```