---
title: "HTMLMeterElement: max property"
short-title: max
slug: Web/API/HTMLMeterElement/max
page-type: web-api-instance-property
browser-compat: api.HTMLMeterElement.max
---

{{ APIRef("HTML DOM") }}

خاصیت **`max`** از رابط {{DOMxRef("HTMLMeterElement")}} مقدار حداکثر (max) عنصر {{htmlelement("meter")}} را به صورت یک عدد اعشاری (floating-point) نمایش می‌دهد. این خاصیت منعکس‌کنندهٔ ویژگی [`max`](/en-US/docs/Web/HTML/Reference/Elements/meter#max) عنصر است، یا اگر `max` تنظیم نشده باشد مقدار `min`، و اگر نه `min` و نه `max` تعریف نشده باشند مقدار `1` را برمی‌گرداند.

این خاصیت را می‌توان مستقیماً نیز مقداردهی کرد، مثلاً برای تنظیم یک مقدار پیش‌فرض بر اساس یک شرط.

## مقدار

یک عدد.

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
console.log(meterElement.max); // 100
--meterElement.max;
console.log(meterElement.max); // 99
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meter")}}
- {{DOMXref("HTMLMeterElement.value")}}
- {{DOMXref("HTMLMeterElement.min")}}
- {{DOMXref("HTMLProgressElement")}}