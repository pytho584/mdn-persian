---
title: "PerformanceElementTiming: id property"
short-title: id
slug: Web/API/PerformanceElementTiming/id
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.id
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`id`** در رابط {{domxref("PerformanceElementTiming")}}، [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عنصر مرتبط را برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

### استفاده از `id`

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) تحت نظارت قرار می‌گیرد. یک {{domxref("PerformanceObserver")}} ثبت شده است تا همهٔ ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های پیش از ایجاد observer استفاده می‌شود. این کار مقدار `myImage` را در کنسول ثبت خواهد کرد که همان [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عنصر تصویر است.

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
      console.log(entry.id);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}