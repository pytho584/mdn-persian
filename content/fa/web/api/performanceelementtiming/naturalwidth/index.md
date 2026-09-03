---
title: "PerformanceElementTiming: naturalWidth property"
short-title: naturalWidth
slug: Web/API/PerformanceElementTiming/naturalWidth
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.naturalWidth
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`naturalWidth`** در رابط {{domxref("PerformanceElementTiming")}} عرض ذاتی عنصر تصویر را بازمی‌گرداند.

## مقدار

یک عدد صحیح بدون علامت ۳۲ بیتی (unsigned long) که عرض ذاتی تصویر است اگر این ویژگی روی یک تصویر اعمال شود؛ برای متن مقدار `0` برمی‌گردد.

## مثال‌ها

### ثبت `naturalWidth`

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) تحت نظارت قرار می‌گیرد. یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا همه ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. فایل تصویر دارای عرض ۱۰۰۰ پیکسل و ارتفاع ۷۵۰ پیکسل است. فراخوانی `entry.naturalWidth` مقدار `1000` را برمی‌گرداند که همان عرض ذاتی بر حسب پیکسل است.

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
      console.log(entry.naturalWidth);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}