---
title: "PointerEvent: tangentialPressure property"
short-title: tangentialPressure
slug: Web/API/PointerEvent/tangentialPressure
page-type: web-api-instance-property
browser-compat: api.PointerEvent.tangentialPressure
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`tangentialPressure`** از رابط {{domxref("PointerEvent")}}، فشار مماسی نرمال‌شدهٔ ورودی اشاره‌گر را نشان می‌دهد (که با نام‌های فشار بشکه‌ای یا [تنش سیلندری](https://en.wikipedia.org/wiki/Cylinder_stress) نیز شناخته می‌شود).

## مقدار

یک `float` که فشار مماسی نرمال‌شدهٔ ورودی اشاره‌گر را در بازهٔ `1-` تا `1` (شامل هر دو) نشان می‌دهد؛ `0` حالت خنثیِ کنترل است.

توجه داشته باشید که برخی سخت‌افزارها فقط مقادیر مثبت در بازهٔ `0` تا `1` را پشتیبانی می‌کنند. برای سخت‌افزاری که فشار مماسی را پشتیبانی نمی‌کند، مقدار این ویژگی `0` خواهد بود.

## مثال‌ها

در این قطعه‌کد، وقتی یک رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} رخ می‌دهد، بسته به مقدار ویژگی `tangentialPressure` آن رویداد، توابع متفاوتی فراخوانی می‌شوند.

```js
someElement.addEventListener("pointerdown", (event) => {
  if (event.tangentialPressure === 0) {
    // No pressure
    process_no_tanPressure(event);
  } else if (event.tangentialPressure === 1) {
    // Maximum pressure
    process_max_tanPressure(event);
  } else {
    // Default
    process_tanPressure(event);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("Touch.force") }}