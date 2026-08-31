---
title: "AnimationEffect: getComputedTiming() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEffect/getComputedTiming"
translated_by: "n8n + AI"
---

---
title: "AnimationEffect: getComputedTiming() method"
short-title: getComputedTiming()
slug: Web/API/AnimationEffect/getComputedTiming
page-type: web-api-instance-method
browser-compat: api.AnimationEffect.getComputedTiming
---

{{ APIRef("Web Animations") }}

متد `getComputedTiming()` در رابط {{domxref("AnimationEffect")}} ویژگی‌های زمان‌بندی محاسبه‌شده را برای این اثر انیمیشن برمی‌گرداند.

> [!NOTE]
> این مقادیر با استایل‌های محاسبه‌شدهٔ یک عنصر که با استفاده از `window.getComputedStyle(elem)` برگردانده می‌شوند، قابل مقایسه هستند.

## نحو

```js-nolint
getComputedTiming()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء که شامل موارد زیر است:

- تمام ویژگی‌های شیء برگشتی از {{domxref("AnimationEffect.getTiming()")}}، با این تفاوت که هر مقدار `"auto"` با مقدار محاسبه‌شده‌ای جایگزین می‌شود که ممکن است به نوع {{domxref("AnimationEffect")}} بستگی داشته باشد.
- ویژگی‌های اضافی زیر:
  - `endTime`
    - : یک `number` که زمان پایان اثر را بر حسب میلی‌ثانیه از شروع اثر نشان می‌دهد. این مقدار برابر است با `activeDuration` به‌علاوهٔ `delay` و `endDelay`.
  - `activeDuration`
    - : یک `number` که مجموع مدت‌زمان را بر حسب میلی‌ثانیه برای همهٔ تکرارهای اثر نشان می‌دهد. این مقدار برابر است با `duration` ضربدر `iterations` (یا صفر اگر آن حاصل‌ضرب {{jsxref("NaN")}} باشد).
  - `localTime`
    - : یک `number` یا `null`.

      مدت زمانی را بر حسب میلی‌ثانیه نشان می‌دهد که اثر اجرا شده است. این مقدار برابر با {{domxref("Animation.currentTime","currentTime")}} انیمیشن مرتبط است، یا اگر اثر با انیمیشنی مرتبط نباشد، `null` است.

  - `progress`
    - : `null` یا یک `number`.

      پیشرفت اثر را در تکرار فعلی‌اش نشان می‌دهد. در آغاز `activeDuration`، این مقدار برابر با بخش کسری `iterationStart` است.

      مقدار معمولاً بین `0` و `1` است، اما بسته به خروجی {{cssxref("easing-function")}} اثر ممکن است خارج از این بازه قرار گیرد. برای مثال، یک تابع نرم‌کننده مانند `cubic-bezier(0.3, 2, 0.6, 2)` پیشرفت زمانی `0.5` را به تقریباً `1.65` تبدیل می‌کند.

      اگر اثر در میانهٔ تکرار نباشد، `null` برمی‌گرداند؛ برای مثال اگر اثر در دوره‌های `delay` یا `endDelay` باشد، اثر تمام شده باشد، یا `localTime` برابر `null` باشد.

  - `currentIteration`
    - : `null` یا یک `number` صحیح.

      شاخص تکرار فعلی را نشان می‌دهد. در آغاز `activeDuration`، این مقدار برابر با بخش صحیح `iterationStart` است.

      هرگاه `progress` برابر `null` باشد، `null` برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationEffect")}}
- {{domxref("Animation")}}