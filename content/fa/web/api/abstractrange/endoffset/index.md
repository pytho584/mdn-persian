---
title: "AbstractRange: endOffset property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/endOffset"
translated_by: "n8n + AI"
---

ویژگی **`endOffset`** در رابط `AbstractRange`، موقعیت (offset) انتهای محدوده (range) را نسبت به گرهٔ پایانی برمی‌گرداند.

برای تغییر موقعیت پایانی، می‌توانید از متد `Range.setEnd()` یا متدی مشابه استفاده کنید.

## مقدار

یک عدد صحیح که تعداد کاراکترها را از ابتدای `Node` مشخص‌شده توسط `endContainer` تا آخرین کاراکتر محدوده نشان می‌دهد.

اگر `endContainer` از نوع `Text`، `Comment` یا `CDATASection` باشد، offset تعداد کاراکترها از ابتدای همان `endContainer` تا نقطهٔ مرزی محدوده است. برای سایر انواع `Node`، `endOffset` شمارهٔ گره‌های فرزند بین ابتدای `endContainer` و نقطهٔ مرزی محدوده خواهد بود.

## مثال

```js
const range = document.createRange();
range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);

const endRangeOffset = range.endOffset;
```