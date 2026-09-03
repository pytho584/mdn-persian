---
title: "PerformanceElementTiming: naturalHeight property"
short-title: naturalHeight
slug: Web/API/PerformanceElementTiming/naturalHeight
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.naturalHeight
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`naturalHeight`** در رابط {{domxref("PerformanceElementTiming")}} ارتفاع ذاتی عنصر تصویر را برمی‌گرداند.

## مقدار

یک عدد صحیح بدون علامت ۳۲ بیتی (unsigned long) که اگر روی یک تصویر اعمال شده باشد، ارتفاع ذاتی تصویر است و برای متن `0` است.

## مثال‌ها

### ثبت `naturalHeight`

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) تحت مشاهده قرار می‌گیرد. یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا تمام ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. فایل تصویر دارای عرض ۱۰۰۰ پیکسل و ارتفاع ۷۵۰ پیکسل است. فراخوانی `entry.naturalHeight` مقدار `750` را برمی‌گرداند که ارتفاع ذاتی بر حسب پیکسل است.

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
      console.log(entry.naturalHeight);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}