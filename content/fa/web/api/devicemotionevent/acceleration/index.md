---
title: "DeviceMotionEvent: acceleration property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent/acceleration"
---

---
title: "DeviceMotionEvent: acceleration property"
short-title: acceleration
slug: Web/API/DeviceMotionEvent/acceleration
page-type: web-api-instance-property
browser-compat: api.DeviceMotionEvent.acceleration
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`acceleration`** در رابط {{domxref("DeviceMotionEvent")}}، شتاب ثبت‌شده توسط دستگاه را بر حسب [متر بر مجذور ثانیه (m/s²)](https://en.wikipedia.org/wiki/Meter_per_second_squared) بازمی‌گرداند. این مقدار شامل اثر نیروی گرانش نمی‌شود، در مقابل {{DOMxRef("DeviceMotionEvent.accelerationIncludingGravity")}} که شامل آن است.

> [!NOTE]
> اگر سخت‌افزار نتواند گرانش را از داده‌های شتاب حذف کند، ممکن است این مقدار در {{DOMxRef("DeviceMotionEvent")}} وجود نداشته باشد. در این حالت، باید به جای آن از {{DOMxRef("DeviceMotionEvent.accelerationIncludingGravity")}} استفاده کنید.

## مقدار

ویژگی `acceleration` یک شیء است که اطلاعاتی درباره شتاب در سه محور در [چارچوب مختصات دستگاه](/en-US/docs/Web/API/Device_orientation_events/Orientation_and_motion_data_explained#device_coordinate_frame) ارائه می‌دهد. هر محور با یک ویژگی جداگانه نمایش داده می‌شود:

- `x`
  - : نشان‌دهنده شتاب در امتداد محور x
- `y`
  - : نشان‌دهنده شتاب در امتداد محور y
- `z`
  - : نشان‌دهنده شتاب در امتداد محور z

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Device orientation events/Detecting device orientation", "تشخیص جهت‌گیری دستگاه", "", "nocode")}}
- {{domxref("Device orientation events/Orientation and motion data explained", "توضیح داده‌های جهت‌گیری و حرکت", "", "nocode")}}
- رویداد {{DOMxRef("Window/devicemotion_event", "devicemotion")}}