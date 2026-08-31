---
title: "CountQueuingStrategy: CountQueuingStrategy() constructor"
short-title: CountQueuingStrategy()
slug: Web/API/CountQueuingStrategy/CountQueuingStrategy
page-type: web-api-constructor
browser-compat: api.CountQueuingStrategy.CountQueuingStrategy
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

سازندهٔ **`CountQueuingStrategy()`** یک نمونه از شیء `CountQueuingStrategy` را می‌سازد و بازمی‌گرداند.

## سینتکس

```js-nolint
new CountQueuingStrategy(options)
```

### پارامترها

- `options`
  - : شیءای با ویژگی زیر:
    - `highWaterMark`
      - : تعداد کل تکه‌هایی (chunks) که می‌توانند در صف داخلی قرار گیرند، پیش از آنکه فشار معکوس (backpressure) اعمال شود.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("CountQueuingStrategy")}}.

### استثناها

هیچکدام.

## مثال‌ها

```js
const queuingStrategy = new CountQueuingStrategy({ highWaterMark: 1 });

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
  queuingStrategy,
);

const size = queuingStrategy.size();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CountQueuingStrategy")}}