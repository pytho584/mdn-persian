---
title: "OrientationSensor: populateMatrix() method"
short-title: populateMatrix()
slug: Web/API/OrientationSensor/populateMatrix
page-type: web-api-instance-method
browser-compat: api.OrientationSensor.populateMatrix
---

{{securecontext_header}}{{APIRef("Sensor API")}}

متد **`populateMatrix()`** در واسط {{domxref("OrientationSensor")}}، ماتریس هدف داده‌شده را بر اساس آخرین خوانش سنسور، با ماتریس چرخش پر می‌کند. ماتریس چرخش در زیر نشان داده شده است.

![فرمول‌های مورد استفاده برای تبدیل چهارگان سنسور به ماتریس داده‌شده.](quaternion_to_rotation_matrix.png)

که در آن:

- W = cos(θ/2)
- X = Vx \* sin(θ/2)
- Y = Vy \* sin(θ/2)
- Z = Vz \* sin(θ/2)

## نحو

```js-nolint
populateMatrix(targetMatrix)
```

از آنجا که {{domxref('OrientationSensor')}} یک کلاس پایه است، `populateMatrix` فقط می‌تواند از یکی از کلاس‌های مشتق‌شده از آن فراخوانی شود.

### پارامترها

- `targetMatrix`
  - : TBD

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// TBD
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```