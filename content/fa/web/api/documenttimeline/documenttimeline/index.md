---
title: "DocumentTimeline: DocumentTimeline() constructor"
short-title: DocumentTimeline()
slug: Web/API/DocumentTimeline/DocumentTimeline
page-type: web-api-constructor
browser-compat: api.DocumentTimeline.DocumentTimeline
---

{{ APIRef("Web Animations") }}

سازنده **`DocumentTimeline()`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) یک نمونه جدید از شی {{domxref("DocumentTimeline")}} ایجاد می‌کند که با سند فعال زمینه مرور فعلی مرتبط است.

## نحو

```js-nolint
new DocumentTimeline(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شی که گزینه‌های زمان‌بندی جدید را مشخص می‌کند. ویژگی‌های زیر در دسترس هستند:
    - `originTime` {{optional_inline}}
      - : یک `number` که زمان صفر را برای {{domxref("DocumentTimeline")}} به عنوان تعداد میلی‌ثانیه نسبت به {{domxref("Performance.timeOrigin")}} مشخص می‌کند. پیش‌فرض `0`.

## مثال‌ها

### زمان مبدأ

یک {{domxref("DocumentTimeline")}} با `originTime` صفر، زمان را از {{domxref("Performance.timeOrigin")}} شروع می‌کند. این همان رفتار {{domxref("Document.timeline")}} است.

```js
const timeline = new DocumentTimeline();
console.log(timeline.currentTime === document.timeline.currentTime); // true
```

تنظیم یک `originTime` غیر صفر، {{domxref("DocumentTimeline")}} را به میزان آن مقدار از {{domxref("Document.timeline")}} جابه‌جا می‌کند:

```js
const offsetTimeline = new DocumentTimeline({ originTime: 500 });
console.log(document.timeline.currentTime - offsetTimeline.currentTime); // 500
```

یک {{domxref("DocumentTimeline")}} نسبی به لحظه فعلی می‌تواند به صورت زیر ساخته شود:

```js
const nowTimeline = new DocumentTimeline({
  originTime: document.timeline.currentTime,
});
console.log(nowTimeline.currentTime); // 0
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationTimeline")}}
- {{domxref("DocumentTimeline")}}