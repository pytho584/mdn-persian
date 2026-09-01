---
title: "HTMLMeterElement: high property"
short-title: high
slug: Web/API/HTMLMeterElement/high
page-type: web-api-instance-property
browser-compat: api.HTMLMeterElement.high
---

{{ APIRef("HTML DOM") }}

ویژگی **`high`** در رابط {{DOMxRef("HTMLMeterElement")}}، مرز بالایی عنصر {{htmlelement("meter")}} را به صورت یک عدد ممیز شناور نشان می‌دهد. این ویژگی، ویژگی [`high`](/en-US/docs/Web/HTML/Reference/Elements/meter#high) عنصر را منعکس می‌کند و در صورت تعریف‌نشدن، مقدار `max` را برمی‌گرداند. مقدار `high` توسط مقادیر `low` و `max` محدود (clamp) می‌شود.

این ویژگی را می‌توان به‌طور مستقیم نیز مقداردهی کرد، مثلاً برای تنظیم یک مقدار پیش‌فرض بر اساس یک شرط خاص.

## مقدار

عددی که نه کمتر از {{DOMxRef("HTMLMeterElement.low")}} و نه بیشتر از {{DOMxRef("HTMLMeterElement.max")}} باشد.

## مثال‌ها

```html
<label for="fuel">سطح سوخت فعلی:</label>
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
console.log(meterElement.high); // 66
++meterElement.high;
console.log(meterElement.high); // 67
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meter")}}
- {{DOMXref("HTMLMeterElement.value")}}
- {{DOMXref("HTMLMeterElement.max")}}
- {{DOMXref("HTMLMeterElement.low")}}
- {{DOMXref("HTMLProgressElement")}}