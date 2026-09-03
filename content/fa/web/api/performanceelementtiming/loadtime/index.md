---
title: "PerformanceElementTiming: loadTime property"
short-title: loadTime
slug: Web/API/PerformanceElementTiming/loadTime
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.loadTime
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`loadTime`** از رابط {{domxref("PerformanceElementTiming")}} برای متن همیشه `0` برمی‌گرداند. برای تصاویر، این ویژگی زمانی را برمی‌گرداند که برابر با جدیدترین زمان بین بارگذاری منبع تصویر و زمان اتصال آن به عنصر است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که `loadTime` عنصر را نشان می‌دهد. برای متن همیشه `0` است.

## مثال‌ها

### ثبت `loadTime`

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) مشاهده می‌شود. یک {{domxref("PerformanceObserver")}} ثبت شده است تا تمام ورودی‌های عملکرد از نوع `"element"` را دریافت کند. پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. فراخوانی `entry.loadTime` زمان بارگذاری عنصر تصویر را برمی‌گرداند.

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
      console.log(entry.loadTime);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}