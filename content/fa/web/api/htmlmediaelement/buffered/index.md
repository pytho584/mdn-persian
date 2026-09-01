---
title: "HTMLMediaElement: buffered property"
---

---
title: "HTMLMediaElement: buffered property"
short-title: buffered
slug: Web/API/HTMLMediaElement/buffered
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.buffered
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`buffered`** از اشیاء {{domxref("HTMLMediaElement")}} یک [شیء `TimeRanges` نرمال‌سازی‌شده](/en-US/docs/Web/API/TimeRanges#normalized_timeranges_objects) جدید برمی‌گرداند که محدوده‌های منبع رسانه‌ای را که در لحظه دسترسی به ویژگی `buffered` توسط عامل کاربر بافر شده‌اند، در صورت وجود، نشان می‌دهد.

## مقدار

یک [شیء `TimeRanges` نرمال‌سازی‌شده](/en-US/docs/Web/API/TimeRanges#normalized_timeranges_objects) جدید که محدوده‌های منبع رسانه‌ای را که در لحظه دسترسی به ویژگی `buffered` توسط عامل کاربر بافر شده‌اند، در صورت وجود، نشان می‌دهد.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.buffered); // TimeRanges { length: 0 }
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLMediaElement")}}: واسطه‌ای که برای تعریف ویژگی `HTMLMediaElement.buffered` استفاده می‌شود.