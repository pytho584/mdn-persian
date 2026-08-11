---
title: "AbstractRange: startContainer property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/startContainer"
translated_by: "n8n + AI"
---

ویژگی فقط خواندنی **`startContainer`** از رابط {{domxref("AbstractRange")}}، {{domxref("Node")}}‌ای را که شروع محدوده درون آن قرار دارد برمی‌گرداند.

برای تغییر موقعیت شروع، از متد {{domxref("Range.setStart()")}} یا متدی مشابه استفاده کنید.

## مقدار

{{domxref("Node")}}‌ای که موقعیت شروع محدوده درون آن قرار دارد.

## مثال

```js
const range = document.createRange();
range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);

const startRangeNode = range.startContainer;
```