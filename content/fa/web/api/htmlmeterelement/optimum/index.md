---
title: "HTMLMeterElement: optimum property"
short-title: optimum
slug: Web/API/HTMLMeterElement/optimum
page-type: web-api-instance-property
browser-compat: api.HTMLMeterElement.optimum
---

{{ APIRef("HTML DOM") }}

خاصیت **`optimum`** از رابط {{DOMxRef("HTMLMeterElement")}} نشان‌دهندهٔ مرز بهینه عنصر {{htmlelement("meter")}} به صورت یک عدد اعشاری است. این خاصیت صفت [`optimum`](/en-US/docs/Web/HTML/Reference/Elements/meter#optimum) عنصر را منعکس می‌کند، یا اگر تعریف نشده باشد، نقطه میانی بین مقادیر `min` و `max` را نشان می‌دهد. مقدار `optimum` توسط مقادیر `min` و `max` محدود می‌شود.

این خاصیت را می‌توان مستقیماً نیز تنظیم کرد، به عنوان مثال برای تعیین یک مقدار پیش‌فرض بر اساس یک شرط.

## مقدار

یک عدد. در صورت عدم تعریف، پیش‌فرض آن نقطه میانی بین {{DOMxRef("HTMLMeterElement.min")}} و {{DOMxRef("HTMLMeterElement.max")}} است.

## مثال‌ها

در این مثال، هیچ مقدار `optimum` تنظیم نشده است.

```html
<label for="review">Star rating:</label>
<meter id="review" min="0" max="10" low="2" high="8" value="9"></meter>
```

اگرچه به صراحت تعریف نشده است، `optimum` پیش‌فرض نقطه میانی بین `min` و `max` است، اما می‌توان آن را به هر مقداری بین `min` و `max` (شامل خود آنها) تنظیم کرد.

```js
const meterElement = document.getElementById("fuel");
console.log(meterElement.optimum); // 5
meterElement.optimum = (meterElement.max + meterElement.optimum) / 2;
console.log(meterElement.optimum); // 7.5
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meter")}}
- {{DOMXref("HTMLMeterElement.value")}}
- {{DOMXref("HTMLMeterElement.high")}}
- {{DOMXref("HTMLMeterElement.low")}}
- {{DOMXref("HTMLProgressElement")}}