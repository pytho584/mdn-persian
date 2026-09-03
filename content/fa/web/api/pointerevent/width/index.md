---
title: "PointerEvent: width property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent/width"
---

---
title: "PointerEvent: width property"
short-title: width
slug: Web/API/PointerEvent/width
page-type: web-api-instance-property
browser-compat: api.PointerEvent.width
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`width`** در رابط {{domxref("PointerEvent")}}، عرض هندسه‌ی تماسِ اشاره‌گر را در امتداد محور x نشان می‌دهد که با واحد پیکسل CSS اندازه‌گیری می‌شود. بسته به منبع دستگاه اشاره‌گر (مانند انگشت)، ممکن است برای یک اشاره‌گر مشخص، هر رویداد مقدار متفاوتی تولید کند.

اگر سخت‌افزار ورودی قادر به گزارش هندسه‌ی تماس به مرورگر نباشد، مقدار `width` به‌صورت پیش‌فرض `1` خواهد بود.

## مقدار

عرض ناحیه‌ی تماس رویداد (بر حسب پیکسل CSS).

## مثال‌ها

این مثال استفاده از ویژگی‌های `width` و {{domxref("PointerEvent.height","height")}} در رابط {{domxref("PointerEvent")}} را برای محاسبه‌ی ناحیه‌ی تماس نشان می‌دهد.

```js
target.addEventListener("pointerdown", (ev) => {
  // Calculate the contact area
  const area = ev.width * ev.height;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}