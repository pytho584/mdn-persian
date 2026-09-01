---
title: "HTMLMeterElement: low property"
---

{{ APIRef("HTML DOM") }}

ویژگی **`low`** از رابط {{DOMxRef("HTMLMeterElement")}} مرز پایینی عنصر {{htmlelement("meter")}} را به صورت یک عدد اعشاری (floating-point) نمایش می‌دهد. این ویژگی منعکس‌کنندهٔ ویژگی [`low`](/en-US/docs/Web/HTML/Reference/Elements/meter#low) عنصر است، یا اگر تعریف نشده باشد، مقدار `min` را نشان می‌دهد. مقدار `low` توسط مقادیر `min` و `max` محدود می‌شود.

این ویژگی را می‌توان مستقیماً نیز تنظیم کرد، مثلاً برای تعیین یک مقدار پیش‌فرض بر اساس یک شرط.

## مقدار

عددی که نه کمتر از {{DOMxRef("HTMLMeterElement.min")}} و نه بیشتر از {{DOMxRef("HTMLMeterElement.max")}} است.

## مثال‌ها

```html
<label for="fuel">Current fuel level:</label>
<meter
  id="fuel"
  min="0"
  max="100"
  low="15"
  high="66"
  optimum="80"
  value="50"></meter>
```

```js
const meterElement = document.getElementById("fuel");
console.log(meterElement.low); // 15
--meterElement.low;
console.log(meterElement.low); // 14
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meter")}}
- {{DOMXref("HTMLMeterElement.value")}}
- {{DOMXref("HTMLMeterElement.min")}}
- {{DOMXref("HTMLMeterElement.high")}}
- {{DOMXref("HTMLProgressElement")}}