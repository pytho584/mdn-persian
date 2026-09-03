---
title: "PerformanceElementTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceElementTiming/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PerformanceElementTiming.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** در رابط {{domxref("PerformanceElementTiming")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ یک نمایش JSON از شیء {{domxref("PerformanceElementTiming")}} برمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("PerformanceElementTiming")}} است.

JSON شامل ویژگی {{domxref("PerformanceElementTiming.element", "element")}} نمی‌شود، زیرا آن از نوع {{domxref("Element")}} است که عملیات `toJSON()` ارائه نمی‌دهد. با این حال، {{domxref("PerformanceElementTiming.id", "id")}} عنصر در آن وجود دارد.

## مثال‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `PerformanceElementTiming` را با اطلاعات مربوط به عنصر تصویر برمی‌گرداند.

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
      console.log(entry.toJSON());
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

این کار یک شیء JSON مانند زیر را ثبت می‌کند:

```json
{
  "name": "image-paint",
  "entryType": "element",
  "startTime": 670894.1000000238,
  "duration": 0,
  "renderTime": 0,
  "loadTime": 670894.1000000238,
  "intersectionRect": {
    "x": 299,
    "y": 76,
    "width": 135,
    "height": 155,
    "top": 76,
    "right": 434,
    "bottom": 231,
    "left": 299
  },
  "identifier": "big-image",
  "naturalWidth": 135,
  "naturalHeight": 155,
  "id": "myImage",
  "url": "https://en.wikipedia.org/static/images/project-logos/enwiki.png"
}
```

برای دریافت رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}