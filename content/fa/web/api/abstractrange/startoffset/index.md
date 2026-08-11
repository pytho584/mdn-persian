---
title: "AbstractRange: startOffset property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/startOffset"
translated_by: "n8n + AI"
---

# ویژگی `startOffset` از `AbstractRange`

ویژگی فقط‌خواندنی **`startOffset`** در رابط {{domxref("AbstractRange")}} مقدار offset را در گرهٔ شروع، نسبت به موقعیت شروع محدوده برمی‌گرداند.

برای تغییر موقعیت شروع، از متد {{domxref("Range.setStart()")}} یا متدی مشابه استفاده کنید.

## مقدار

مقداری صحیح که تعداد کاراکترها از ابتدای {{domxref("Node")}} مشخص‌شده توسط {{domxref("AbstractRange.startContainer", "startContainer")}} تا نقطه‌ای که اولین کاراکتر محدوده قرار دارد را نشان می‌دهد.

اگر `startContainer` از نوع {{domxref("Node")}}‌های {{domxref("Text")}}، {{domxref("Comment")}} یا {{domxref("CDATASection")}} باشد، offset تعداد کاراکترها از ابتدای `startContainer` تا نقطهٔ مرزی محدوده است. برای انواع دیگر {{domxref("Node")}}، `startOffset` تعداد گره‌های فرزند بین ابتدای `startContainer` و نقطهٔ مرزی محدوده را مشخص می‌کند.

## مثال

```js
const range = document.createRange();
range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);

const startRangeOffset = range.startOffset;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}