---
title: "PerformanceElementTiming: intersectionRect property"
short-title: intersectionRect
slug: Web/API/PerformanceElementTiming/intersectionRect
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.intersectionRect
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`intersectionRect`** در رابط {{domxref("PerformanceElementTiming")}}، مستطیل عنصر را درون viewport برمی‌گرداند.

## مقدار

یک {{domxref("DOMRectReadOnly")}} که مستطیل عنصر درون viewport است.

برای تصاویر نمایش‌داده‌شده، این مستطیل نمایش تصویر درون viewport است. برای متن، این مستطیل نمایش گره (node) درون viewport است. این مقدار کوچک‌ترین مستطیلی است که包含了 اتحاد همهٔ گره‌های متنی متعلق به عنصر را در بر می‌گیرد.

## مثال‌ها

### ثبت `intersectionRect`

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) مشاهده می‌شود. یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا تمام ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. فراخوانی `entry.intersectionRect` یک شیء {{domxref("DOMRectReadOnly")}} شامل مستطیل نمایش تصویر برمی‌گرداند.

```html
<img
  src="image.jpg"
  alt="a nice image"
  elementtiming="big-image"
  id="myImage" />
```

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.identifier === "big-image") {
      console.log(entry.intersectionRect);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}