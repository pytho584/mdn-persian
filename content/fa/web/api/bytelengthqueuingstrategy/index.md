---
title: ByteLengthQueuingStrategy
source: "https://developer.mozilla.org/en-US/docs/Web/API/ByteLengthQueuingStrategy"
translated_by: "n8n + AI"
---

---
title: ByteLengthQueuingStrategy
slug: Web/API/ByteLengthQueuingStrategy
page-type: web-api-interface
browser-compat: api.ByteLengthQueuingStrategy
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

**`ByteLengthQueuingStrategy`** واسط (interface) از [Streams API](/en-US/docs/Web/API/Streams_API) یک استراتژی صف‌بندی بر اساس طول بایت داخلی فراهم می‌کند که می‌تواند هنگام ساخت استریم‌ها استفاده شود.

## سازنده (Constructor)

- {{domxref("ByteLengthQueuingStrategy.ByteLengthQueuingStrategy", "ByteLengthQueuingStrategy()")}}
  - : یک نمونه جدید از شیء `ByteLengthQueuingStrategy` ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("ByteLengthQueuingStrategy.highWaterMark")}} {{ReadOnlyInline}}
  - : تعداد کل بایت‌هایی که می‌توانند در صف داخلی قبل از اعمال [backpressure](/en-US/docs/Web/API/Streams_API/Concepts#backpressure) نگهداری شوند.

## روش‌های نمونه (Instance methods)

- {{domxref("ByteLengthQueuingStrategy.size()")}}
  - : ویژگی `byteLength` داده‌های (chunk) داده شده را برمی‌گرداند.

## نمونه‌ها

```js
const queueingStrategy = new ByteLengthQueuingStrategy({ highWaterMark: 1024 });

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
  queueingStrategy,
);

const size = queueingStrategy.size(chunk);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Streams API", "Streams API", "", "nocode")}}
- [صف‌های داخلی و استراتژی‌های صف‌بندی](/en-US/docs/Web/API/Streams_API/Concepts#internal_queues_and_queuing_strategies)
- سازنده {{domxref("ByteLengthQueuingStrategy.ByteLengthQueuingStrategy", "ByteLengthQueuingStrategy()")}}