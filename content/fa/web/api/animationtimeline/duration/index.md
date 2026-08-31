---
title: "AnimationTimeline: duration property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationTimeline/duration"
translated_by: "n8n + AI"
---

---
title: "AnimationTimeline: duration property"
short-title: duration
slug: Web/API/AnimationTimeline/duration
page-type: web-api-instance-property
browser-compat: api.AnimationTimeline.duration
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی **`duration`** در رابط {{domxref("AnimationTimeline")}} از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)، حداکثر مقدار این خط زمانی (timeline) را برمی‌گرداند یا `null`.

توجه داشته باشید که رابط‌های مشتق‌شده {{domxref("ViewTimeline")}} و {{domxref("ScrollTimeline")}} همیشه مدت‌زمان ۱۰۰٪ را برمی‌گردانند، در حالی که {{domxref("DocumentTimeline")}} مدت‌زمانی ندارد و `null` برمی‌گرداند.

## مقدار

یک عدد که نشان‌دهنده مدت‌زمان خط زمانی (حداکثر مقدار برای این خط زمانی) است یا `null`.

## مثال‌ها

### مدت‌زمان خط زمانی نمای (View Timeline)

{{domxref("ViewTimeline")}} همیشه مدت‌زمان ۱۰۰٪ را به صورت یک {{domxref("CSSUnitValue")}} برمی‌گرداند.

```js
const subject = document.querySelector(".subject");
const timeline = new ViewTimeline({
  subject,
  axis: "block",
});

timeline.duration; // CSSUnitValue { value: 100, unit: "percent" }
```

### مدت‌زمان خط زمانی پیمایش (Scroll Timeline)

{{domxref("ScrollTimeline")}} همیشه مدت‌زمان ۱۰۰٪ را به صورت یک {{domxref("CSSUnitValue")}} برمی‌گرداند.

```js
const timeline = new ScrollTimeline({
  source: document.documentElement,
  axis: "block",
});

timeline.duration; // CSSUnitValue { value: 100, unit: "percent" }
```

### مدت‌زمان خط زمانی سند (Document Timeline)

{{domxref("DocumentTimeline")}} مدت‌زمانی ندارد.

```js
document.timeline.duration; // null
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationTimeline")}}
- {{domxref("DocumentTimeline")}} این ویژگی را به ارث می‌برد
- {{domxref("ScrollTimeline")}} این ویژگی را به ارث می‌برد
- {{domxref("ViewTimeline")}} این ویژگی را به ارث می‌برد
```