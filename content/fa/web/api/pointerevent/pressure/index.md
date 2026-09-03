---
title: "PointerEvent: pressure property"
short-title: pressure
slug: Web/API/PointerEvent/pressure
page-type: web-api-instance-property
browser-compat: api.PointerEvent.pressure
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`pressure`** در رابطِ {{domxref("PointerEvent")}}، فشار نرمال‌شدهٔ ورودیِ اشاره‌گر را نشان می‌دهد.

## مقدار

مقدار فشار نرمال‌شدهٔ ورودیِ اشاره‌گر در بازهٔ `0` تا `1` است؛ جایی که `0` و `1` به‌ترتیب کمترین و بیشترین فشاری را نشان می‌دهند که سخت‌افزار قادر به تشخیص آن است. برای سخت‌افزارهایی که فشار را پشتیبانی نمی‌کنند، مانند ماوس، این مقدار وقتی اشاره‌گر در حالتِ دکمه‌های فعال (active buttons state) قرار دارد `0.5` و در غیر این صورت `0` است.

## مثال‌ها

در این قطعه‌کد، وقتی رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} رخ می‌دهد، بسته به مقدارِ ویژگیِ `pressure` در رویداد، توابع متفاوتی فراخوانی می‌شوند.

```js
someElement.addEventListener("pointerdown", (event) => {
  if (event.pressure === 0) {
    // No pressure
    process_no_pressure(event);
  } else if (event.pressure === 1) {
    // Maximum pressure
    process_max_pressure(event);
  } else {
    // Default
    processPressure(event);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("Touch.force") }}