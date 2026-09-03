---
title: "PressureRecord: state property"
---

---
title: "PressureRecord: state property"
short-title: state
slug: Web/API/PressureRecord/state
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PressureRecord.state
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

ویژگی فقطخواندنی **`state`** یک رشته است که وضعیت فشارِ ثبت‌شده را نشان می‌دهد.

## Value

یک رشته که وضعیت فشارِ ثبت‌شده را نشان می‌دهد. Compute Pressure API از وضعیت‌های فشارِ قابل‌خواندن برای انسان استفاده می‌کند که معانی زیر را دارند (همچنین به [specification](https://w3c.github.io/compute-pressure/#pressure-states) مراجعه کنید):

- ⚪ `"nominal"`: شرایط دستگاه هدف در سطح قابل‌قبولی است و هیچ اثر نامطلوب محسوسی بر کاربر ندارد.
- 🟢 `"fair"`: فشار، دما و/یا مصرف انرژی دستگاه هدف اندکی افزایش یافته است و به‌طور بالقوه می‌تواند عمر باتری را کاهش دهد و فن‌ها (یا سیستم‌های دارای فن) را فعال و قابل‌شنیدن کند. جدا از این، دستگاه هدف بدون نقص کار می‌کند و می‌تواند کارهای بیشتری را بر عهده بگیرد.
- 🟡 `"serious"`: فشار، دما و/یا مصرف انرژی دستگاه هدف به‌طور مداوم و به‌شدت افزایش یافته است. ممکن است سیستم به‌عنوان اقدامی متقابل برای کاهش حرارت، throttling (کاهش سرعت) انجام دهد.
- 🔴 `"critical"`: دمای دستگاه یا سیستم هدف به‌طور قابل‌توجهی افزایش یافته است و برای جلوگیری از هرگونه مشکل احتمالی، نیاز به خنک‌سازی دارد.

## Examples

در مثال زیر، مقدار ویژگی `state` را در callback (تابع بازگشتی) مشاهده‌گر فشار ثبت می‌کنیم.

```js
function callback(records) {
  const lastRecord = records[records.length - 1];
  console.log(`Current pressure is ${lastRecord.state}`);
}

try {
  const observer = new PressureObserver(callback);
  await observer.observe("cpu", {
    sampleInterval: 1000, // 1000ms
  });
} catch (error) {
  // report error setting up the observer
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}