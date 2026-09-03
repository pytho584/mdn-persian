---
title: "Navigator: maxTouchPoints property"
short-title: maxTouchPoints
slug: Web/API/Navigator/maxTouchPoints
page-type: web-api-instance-property
browser-compat: api.Navigator.maxTouchPoints
---

{{APIRef("HTML DOM")}}

خاصیتِ فقط‌خواندنیِ **`maxTouchPoints`** در واسطِ {{domxref("Navigator")}}، حداکثر تعداد نقاط تماسِ همزمانی را برمی‌گرداند که توسط دستگاه فعلی پشتیبانی می‌شود.

## مقدار

یک عدد.

این مقدار به سخت‌افزار وابسته است. رایانه‌های رومیزی بدون صفحه‌لمسی (مک، ویندوز و لینوکس) مقدار ۰ را برمی‌گردانند، در حالی که گوشی‌های هوشمند (اندروید و iOS) معمولاً مقدار ۵ را برمی‌گردانند.

## مثال

```js
if (navigator.maxTouchPoints > 1) {
  // Device supports tracking at least 2 touch points; offer complex
  // interaction gestures such as swiping with two/three fingers
} else {
  // Device only has 1 touch point or is not a touch screen.
  // Offer basic gestures such as dragging and clicking
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
