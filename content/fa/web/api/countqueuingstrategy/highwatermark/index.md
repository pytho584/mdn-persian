---
title: "CountQueuingStrategy: highWaterMark property"
---

---
title: "CountQueuingStrategy: highWaterMark property"
short-title: highWaterMark
slug: Web/API/CountQueuingStrategy/highWaterMark
page-type: web-api-instance-property
browser-compat: api.CountQueuingStrategy.highWaterMark
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

خاصیت فقط خواندنی **`CountQueuingStrategy.highWaterMark`** تعداد کل chunk‌هایی (بازه‌های داده) را برمی‌گرداند که می‌توانند در صف داخلی قبل از اعمال فشار برگشتی (backpressure) قرار بگیرند.

## مقدار

یک عدد صحیح که تعداد chunk‌ها را نشان می‌دهد.

## مثال

```js
const queueingStrategy = new CountQueuingStrategy({ highWaterMark: 1 });

const readableStream = new ReadableStream(
  {
    start(controller) {
      // …
    },
    pull(controller) {
      // …
    },
    cancel(err) {
      console.log("stream error:", err);
    },
  },
  queuingStrategy,
);

const size = queuingStrategy.size(chunk);
console.log(`highWaterMark value: ${queuingStrategy.highWaterMark}$`);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- سازنده {{domxref("CountQueuingStrategy.CountQueuingStrategy", "CountQueuingStrategy()")}}