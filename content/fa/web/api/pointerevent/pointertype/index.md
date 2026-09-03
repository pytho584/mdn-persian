---
title: "PointerEvent: pointerType property"
---

---
title: "PointerEvent: pointerType property"
short-title: pointerType
slug: Web/API/PointerEvent/pointerType
page-type: web-api-instance-property
browser-compat: api.PointerEvent.pointerType
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`pointerType`** از رابط {{domxref("PointerEvent")}} نوع دستگاهی (ماوس، قلم یا لمس) را مشخص می‌کند که باعث وقوع یک رویداد اشارهٔ مشخص شده است.

## مقدار

نوع اشاره‌گرِ رویداد. مقادیر پشتیبانی‌شده، رشته‌های زیر هستند:

- `"mouse"`
  - : رویداد توسط یک دستگاه ماوس تولید شده است.
- `"pen"`
  - : رویداد توسط یک قلم یا stylus تولید شده است.
- `"touch"`
  - : رویداد در اثر لمس، مثلاً با انگشت، تولید شده است.

اگر مرورگر نتواند نوع دستگاه را تشخیص دهد، مقدار می‌تواند یک رشتهٔ خالی (`""`) باشد. اگر مرورگر از انواع دیگری از دستگاه‌های اشاره‌گر به‌جز موارد بالا پشتیبانی کند، مقدار باید دارای پیشوند فروشنده (_vendor-prefixed_) باشد تا از تداخل نام‌ها میان انواع مختلف دستگاه جلوگیری شود.

## مثال‌ها

این مثال نشان می‌دهد که چگونه از مقدار ویژگی `pointerType` برای فراخوانیِ تابعِ پردازشِ متناظر با نوع اشاره‌گر استفاده می‌شود.

```js
targetElement.addEventListener("pointerdown", (event) => {
  // Call the appropriate pointer type handler
  switch (event.pointerType) {
    case "mouse":
      process_pointer_mouse(event);
      break;
    case "pen":
      process_pointer_pen(event);
      break;
    case "touch":
      process_pointer_touch(event);
      break;
    default:
      console.log(`pointerType ${event.pointerType} is not supported`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}