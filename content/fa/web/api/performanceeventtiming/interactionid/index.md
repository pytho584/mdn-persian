---
title: "PerformanceEventTiming: interactionId property"
short-title: interactionId
slug: Web/API/PerformanceEventTiming/interactionId
page-type: web-api-instance-property
browser-compat: api.PerformanceEventTiming.interactionId
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`interactionId`** در رابط (interface) {{domxref("PerformanceEventTiming")}} یک شناسه برمی‌گرداند که به‌طور یکتا یک تعامل کاربری را مشخص می‌کند که مجموعه‌ای از رویدادهای مرتبط را فعال کرده‌است.

## مقدار

یک عدد. برای انواع رویدادهایی که شناسه تعامل برای آن‌ها محاسبه نمی‌شود، مقدار ۰ است.

## توضیحات

هنگامی که کاربر با یک صفحه وب تعامل می‌کند، یک تعامل کاربری (مثلاً کلیک) معمولاً دنباله‌ای از رویدادها مانند `pointerdown`، `pointerup` و `click` را فعال می‌کند. برای اندازه‌گیری تأخیر این سری رویدادها، همه آن‌ها `interactionId` یکسانی دارند.

`interactionId` فقط برای انواع رویدادهای زیر که متعلق به یک تعامل کاربری هستند محاسبه می‌شود. در غیر این صورت مقدار آن `0` است.

| انواع رویداد                                                                                                                                               | تعامل کاربری        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- |
| {{domxref("Element/pointerdown_event", "pointerdown")}}, {{domxref("Element/pointerup_event", "pointerup")}}, {{domxref("Element/click_event", "click")}} | کلیک / لمس / کشیدن |
| {{domxref("Element/keydown_event", "keydown")}}, {{domxref("Element/keyup_event", "keyup")}}                                                              | فشردن کلید         |

`interactionId` همچنین برای محاسبه معیار {{glossary("Interaction to next paint")}} مورد نیاز است که به تحلیل پاسخگویی به تعامل کاربر در طول عمر یک صفحه کمک می‌کند.

## مثال‌ها

### استفاده از interactionId

مثال زیر مدت‌زمان رویدادها را برای همه رویدادهای مربوط به یک تعامل جمع‌آوری می‌کند. سپس می‌توان از نقشه `eventLatencies` برای یافتن رویدادهای با بیشترین مدت‌زمان برای یک تعامل کاربری استفاده کرد، به‌عنوان مثال.

```js
// The key is the interaction ID.
let eventLatencies = {};

const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.interactionId > 0) {
      const interactionId = entry.interactionId;
      if (!eventLatencies.has(interactionId)) {
        eventLatencies[interactionId] = [];
      }
      eventLatencies[interactionId].push(entry.duration);
    }
  });
});

observer.observe({ type: "event", buffered: true });

// Log events with maximum event duration for a user interaction
Object.entries(eventLatencies).forEach(([k, v]) => {
  console.log(Math.max(...v));
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}