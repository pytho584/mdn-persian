---
title: CountQueuingStrategy
slug: Web/API/CountQueuingStrategy
page-type: web-api-interface
browser-compat: api.CountQueuingStrategy
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

رابط **`CountQueuingStrategy`** در [API Streams](/en-US/docs/Web/API/Streams_API) یک استراتژی صف‌بندی داخلی بر اساس شمارش تکه‌ها (chunk counting) ارائه می‌دهد که می‌توان هنگام ساخت استریم‌ها از آن استفاده کرد.

## سازنده

- {{domxref("CountQueuingStrategy.CountQueuingStrategy", "CountQueuingStrategy()")}}
  - : یک نمونه جدید از شیء `CountQueuingStrategy` ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("CountQueuingStrategy.highWaterMark")}} {{ReadOnlyInline}}
  - : تعداد کل تکه‌هایی که می‌توانند قبل از اعمال [backpressure](/en-US/docs/Web/API/Streams_API/Concepts#backpressure) در صف داخلی قرار گیرند.

## روش‌های نمونه

- {{domxref("CountQueuingStrategy.size()")}}
  - : همیشه `1` را برمی‌گرداند.

## مثال‌ها

```js
const queueingStrategy = new CountQueuingStrategy({ highWaterMark: 1 });

const writableStream = new WritableStream(
  {
    // Implement the sink
    write(chunk) {
      // …
    },
    close() {
      // …
    },
    abort(err) {
      console.log("Sink error:", err);
    },
  },
  queueingStrategy,
);

const size = queueingStrategy.size();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Streams API", "Streams API", "", "nocode")}}
- سازنده {{domxref("CountQueuingStrategy.CountQueuingStrategy", "CountQueuingStrategy()")}}
- [صف‌های داخلی و استراتژی‌های صف‌بندی](/en-US/docs/Web/API/Streams_API/Concepts#internal_queues_and_queuing_strategies)