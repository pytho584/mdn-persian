---
title: "HTMLMeterElement: min property"
short-title: min
slug: Web/API/HTMLMeterElement/min
page-type: web-api-instance-property
browser-compat: api.HTMLMeterElement.min
---

{{ APIRef("HTML DOM") }}

خاصیت **`min`** از رابط {{DOMxRef("HTMLMeterElement")}}، مقدار حداقل عنصر {{htmlelement("meter")}} را به صورت یک عدد اعشاری نمایش می‌دهد. این خاصیت منعکس‌کننده ویژگی [`min`](/en-US/docs/Web/HTML/Reference/Elements/meter#min) عنصر است، یا اگر `min` تعریف نشده باشد، مقدار `0` را برمی‌گرداند.

این خاصیت همچنین می‌تواند مستقیماً تنظیم شود، مثلاً برای تنظیم یک مقدار پیش‌فرض بر اساس یک شرط.

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
console.log(meterElement.min); // 0
++meterElement.min;
console.log(meterElement.min); // 1
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meter")}}
- {{DOMXref("HTMLMeterElement.value")}}
- {{DOMXref("HTMLMeterElement.max")}}
- {{DOMXref("HTMLProgressElement")}}