---
title: "AbsoluteOrientationSensor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbsoluteOrientationSensor"
translated_by: "n8n + AI"
---

# AbsoluteOrientationSensor

رابط **`AbsoluteOrientationSensor`** در [Sensor APIها](/en-US/docs/Web/API/Sensor_APIs) جهت‌گیری فیزیکی دستگاه را نسبت به دستگاه مختصات مرجع زمین توصیف می‌کند.

برای استفاده از این حسگر، کاربر باید از طریق [Permissions API](/en-US/docs/Web/API/Permissions_API) به حسگرهای `'accelerometer'`، `'gyroscope'` و `'magnetometer'` دستگاه دسترسی بدهد.

ممکن است این قابلیت توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) که روی سرور تنظیم شده مسدود شود.

## سازنده

- [`AbsoluteOrientationSensor()`](/en-US/docs/Web/API/AbsoluteOrientationSensor/AbsoluteOrientationSensor)
  - : یک شیء جدید `AbsoluteOrientationSensor` می‌سازد.

## پراپرتی‌های نمونه

_پراپرتی اختصاصی‌ای ندارد؛ پراپرتی‌ها را از نیاکان خود یعنی [`OrientationSensor`](/en-US/docs/Web/API/OrientationSensor) و [`Sensor`](/en-US/docs/Web/API/Sensor) به ارث می‌برد._

## متدهای نمونه

_متد اختصاصی‌ای ندارد؛ متدها را از نیاکان خود یعنی [`OrientationSensor`](/en-US/docs/Web/API/OrientationSensor) و [`Sensor`](/en-US/docs/Web/API/Sensor) به ارث می‌برد._

## رویدادها

_رویداد اختصاصی‌ای ندارد؛ رویدادها را از جد خود یعنی [`Sensor`](/en-US/docs/Web/API/Sensor) به ارث می‌برد._

## مثال‌ها

### مثال پایه

مثال زیر که تا حدی بر اساس [دموی Intel Orientation Phone](https://intel.github.io/generic-sensor-demos/orientation-phone/) است، یک `AbsoluteOrientationSensor` با فرکانس ۶۰ بار در ثانیه نمونه‌سازی می‌کند. در هر بار خواندن از [`OrientationSensor.quaternion`](/en-US/docs/Web/API/OrientationSensor/quaternion) برای چرخاندن یک مدل بصری از تلفن استفاده می‌شود.

```js
const options = { frequency: 60, referenceFrame: "device" };
const sensor = new AbsoluteOrientationSensor(options);

sensor.addEventListener("reading", () => {
  // model is a Three.js object instantiated elsewhere.
  model.quaternion.fromArray(sensor.quaternion).inverse();
});
sensor.addEventListener("error", (event) => {
  if (event.error.name === "NotReadableError") {
    console.log("Sensor is not available.");
  }
});
sensor.start();
```

### مثال مجوزها

استفاده از حسگرهای جهت‌یابی نیازمند درخواست مجوز برای چندین حسگر دستگاه است. از آنجا که رابط [`Permissions`](/en-US/docs/Web/API/Permissions) از promiseها استفاده می‌کند، یک روش مناسب برای درخواست مجوزها به‌کارگیری {{jsxref('Promise.all')}} است.

```js
const sensor = new AbsoluteOrientationSensor();
Promise.all([
  navigator.permissions.query({ name: "accelerometer" }),
  navigator.permissions.query({ name: "magnetometer" }),
  navigator.permissions.query({ name: "gyroscope" }),
]).then((results) => {
  if (results.every((result) => result.state === "granted")) {
    sensor.start();
    // …
  } else {
    console.log("No permissions to use AbsoluteOrientationSensor.");
  }
});
```