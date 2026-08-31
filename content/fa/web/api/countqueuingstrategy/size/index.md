---
title: "CountQueuingStrategy: size() method"
short-title: size()
slug: Web/API/CountQueuingStrategy/size
page-type: web-api-instance-method
browser-compat: api.CountQueuingStrategy.size
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

متد **`size()`** از رابط {{domxref("CountQueuingStrategy")}} همیشه `1` را برمی‌گرداند، به طوری که اندازه کل صف، تعداد تکه‌های موجود در صف است.

## نحو (Syntax)

```js-nolint
size()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

`1`.

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

## جستارهای وابسته

- سازنده {{domxref("CountQueuingStrategy.CountQueuingStrategy", "CountQueuingStrategy()")}}