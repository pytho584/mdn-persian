---
title: "Accelerometer"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Accelerometer"
translated_by: "n8n + AI"
---

# Accelerometer

رابط **`Accelerometer`** از [Sensor APIs](/en-US/docs/Web/API/Sensor_APIs) در هر بار خواندن، شتاب وارد‌شده به دستگاه را در امتداد هر سه محور ارائه می‌دهد.

برای استفاده از این حسگر، کاربر باید از طریق [Permissions API](/en-US/docs/Web/API/Permissions_API) مجوز `'accelerometer'` را به حسگر دستگاه بدهد.

این قابلیت ممکن است توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) که روی سرور شما تنظیم شده مسدود شود.

## Constructor

- `Accelerometer()` (تجربی)
  - : یک شیء جدید `Accelerometer` ایجاد می‌کند.

## Instance properties

علاوه بر ویژگی‌های فهرست‌شده در زیر، `Accelerometer` ویژگی‌ها را از رابط‌های والد خود، `Sensor` و `EventTarget`، به ارث می‌برد.

- `Accelerometer.x` (فقط‌خواندنی) (تجربی)
  - : یک عدد `double` برمی‌گرداند که شتاب دستگاه در راستای محور x دستگاه را نشان می‌دهد.
- `Accelerometer.y` (فقط‌خواندنی) (تجربی)
  - : یک عدد `double` برمی‌گرداند که شتاب دستگاه در راستای محور y دستگاه را نشان می‌دهد.
- `Accelerometer.z` (فقط‌خواندنی) (تجربی)
  - : یک عدد `double` برمی‌گرداند که شتاب دستگاه در راستای محور z دستگاه را نشان می‌دهد.

## Instance methods

_`Accelerometer` متد خاص خود را ندارد. با این حال، متدها را از رابط‌های والد خود، `Sensor` و `EventTarget`، به ارث می‌برد._

## Events

_`Accelerometer` رویداد خاص خود را ندارد. با این حال، رویدادها را از رابط والد خود، `Sensor`، به ارث می‌برد._

## Example

شتاب معمولاً در callback رویداد `reading` خوانده می‌شود. در مثال زیر، این کار شصت بار در ثانیه انجام می‌شود.

```js
const acl = new Accelerometer({ frequency: 60 });
acl.addEventListener("reading", () => {
  console.log(`Acceleration along the X-axis ${acl.x}`);
  console.log(`Acceleration along the Y-axis ${acl.y}`);
  console.log(`Acceleration along the Z-axis ${acl.z}`);
});

acl.start();
```