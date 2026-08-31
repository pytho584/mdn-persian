---
title: "CanvasRenderingContext2D: isContextLost() method"
short-title: isContextLost()
slug: Web/API/CanvasRenderingContext2D/isContextLost
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.isContextLost
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.isContextLost()`** از Canvas 2D API مقدار `true` را برمی‌گرداند اگر زمینه‌ی رندرینگ از دست رفته باشد (و هنوز بازنشانی نشده باشد). این وضعیت ممکن است به دلیل خرابی درایور، اتمام حافظه و موارد مشابه رخ دهد.

اگر عامل کاربر (user agent) تشخیص دهد که حافظه‌ی پشتیبان (backing storage) canvas از دست رفته است، رویداد [`contextlost`](/en-US/docs/Web/API/HTMLCanvasElement/contextlost_event) را روی [`HTMLCanvasElement`](/en-US/docs/Web/API/HTMLCanvasElement) مرتبط فعال می‌کند. اگر این رویداد لغو نشود (cancelled)، سعی می‌کند حافظه‌ی پشتیبان را به حالت پیش‌فرض بازنشانی کند (این معادل فراخوانی {{domxref("CanvasRenderingContext2D.reset()")}} است). در صورت موفقیت، رویداد [`contextrestored`](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event) را فعال می‌کند که نشان می‌دهد زمینه آماده است تا دوباره مقداردهی اولیه و رسم شود.

## Syntax

```js-nolint
isContextLost()
```

### پارامترها

هیچ.

### مقدار بازگشتی

`true` اگر زمینه‌ی رندرینگ از دست رفته باشد؛ در غیر این صورت `false`.

### مثال‌ها

```js
const ctx = canvas.getContext("2d");

if (ctx.isContextLost()) {
  console.log("Context is lost");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- رویداد [`HTMLCanvasElement: contextlost`](/en-US/docs/Web/API/HTMLCanvasElement/contextlost_event)
- رویداد [`HTMLCanvasElement: contextrestored`](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event)