---
title: "HTMLMeterElement: value property"
---

{{ APIRef("HTML DOM") }}

خاصیت **`value`** از رابط {{DOMxRef("HTMLMeterElement")}} مقدار فعلی عنصر {{htmlelement("meter")}} را به صورت یک عدد اعشاری نمایش می‌دهد. این خاصیت منعکس‌کنندهٔ ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/meter#value) عنصر است. اگر هیچ `value`ای تنظیم نشده باشد، مقدار {{DOMxRef("HTMLMeterElement.min")}} یا `0` (هر کدام بزرگتر است) خواهد بود.

این خاصیت را می‌توان مستقیماً نیز تنظیم کرد، مثلاً برای تعیین یک مقدار پیش‌فرض بر اساس یک شرط.

## مقدار

یک عدد. به طور پیش‌فرض، اگر تعریف نشده باشد، برابر با {{DOMxRef("HTMLMeterElement.min")}} یا `0` (هر کدام بزرگتر است) خواهد بود.

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
console.log(meterElement.value); // 50
--meterElement.value;
console.log(meterElement.value); // 49
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meter")}}
- {{DOMXref("HTMLMeterElement.min")}}
- {{DOMXref("HTMLProgressElement")}}