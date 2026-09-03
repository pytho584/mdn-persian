---
title: "PerformanceElementTiming: url property"
short-title: url
slug: Web/API/PerformanceElementTiming/url
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.url
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیتِ فقط‌خواندنی **`url`** در رابط {{domxref("PerformanceElementTiming")}}، نشانی اولیه درخواست منبع را زمانی که عنصر یک تصویر است، برمی‌گرداند.

## مقدار

یک رشته که نشانی اولیه درخواست منبع برای تصاویر است، یا برای متن `0` است.

## مثال‌ها

### ثبت `url`

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) مشاهده می‌شود. یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا همه ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. فراخوانی `entry.url` مقدار `https://example.com/image.jpg` را برمی‌گرداند.

```html
<img
  src="https://example.com/image.jpg"
  alt="a nice image"
  elementtiming="big-image"
  id="myImage" />
```

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.identifier === "big-image") {
      console.log(entry.url);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```