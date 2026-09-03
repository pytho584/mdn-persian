---
title: "PointerEvent: twist property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent/twist"
---

---
title: "PointerEvent: twist property"
short-title: twist
slug: Web/API/PointerEvent/twist
page-type: web-api-instance-property
browser-compat: api.PointerEvent.twist
---

{{ APIRef("Pointer Events") }}

خاصیتِ خواندنی **`twist`** در رابط {{domxref("PointerEvent")}} میزان چرخشِ ساعتگردِ نشانگر (مثلاً قلمِ دیجیتال) را حول محور اصلی‌اش، بر حسب درجه، نشان می‌دهد.

## مقدار

یک مقدار از نوع `long` که میزان چرخش واردشده بر مبدلِ (نشانگر) را بر حسب درجه نشان می‌دهد. این مقدار در بازهٔ `0` تا `359` است. برای دستگاه‌هایی که `twist` را گزارش نمی‌کنند، مقدار `0` است.

## مثال‌ها

هنگامی که رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} رخ می‌دهد، بسته به مقدار خاصیت `twist` رویداد، توابع مختلفی فراخوانی می‌شوند.

```js
someElement.addEventListener("pointerdown", (event) => {
  if (event.twist === 0) {
    // بدون چرخش
    process_no_twist(event);
  } else {
    // حالت پیش‌فرض
    process_twist(event);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("Touch.force") }}