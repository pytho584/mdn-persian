---
title: "DeviceMotionEvent: accelerationIncludingGravity property"
short-title: accelerationIncludingGravity
slug: Web/API/DeviceMotionEvent/accelerationIncludingGravity
page-type: web-api-instance-property
browser-compat: api.DeviceMotionEvent.accelerationIncludingGravity
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`accelerationIncludingGravity`** در رابط {{domxref("DeviceMotionEvent")}} مقدار شتاب ثبت‌شده توسط دستگاه را بر حسب [متر بر مجذور ثانیه (m/s²)](https://en.wikipedia.org/wiki/Meter_per_second_squared) برمی‌گرداند. برخلاف {{DOMxRef("DeviceMotionEvent.acceleration")}} که اثر گرانش را جبران می‌کند، مقدار این ویژگی مجموع شتاب ناشی از حرکت کاربر و شتابی برابر و مخالف با شتاب ناشی از گرانش است. به عبارت دیگر، این ویژگی [نیروی g](https://en.wikipedia.org/wiki/G-Force) را اندازه‌گیری می‌کند. در عمل، این مقدار نشان‌دهنده داده‌های خام اندازه‌گیری‌شده توسط [شتاب‌سنج](https://en.wikipedia.org/wiki/Accelerometer) است.

این مقدار معمولاً به اندازه {{DOMxRef("DeviceMotionEvent.acceleration")}} مفید نیست، اما ممکن است تنها مقداری باشد که در دستگاه‌هایی که قادر به حذف گرانش از داده‌های شتاب نیستند (مانند دستگاه‌های بدون ژیروسکوپ) در دسترس باشد.

> [!NOTE]
> نام `accelerationIncludingGravity` ممکن است گمراه‌کننده باشد. این ویژگی شتاب _شامل اثرات_ گرانش را نشان می‌دهد. مثلاً اگر دستگاهی به صورت افقی روی یک سطح صاف قرار گرفته باشد و صفحه نمایش آن رو به بالا باشد، گرانش در امتداد محور Z برابر ۹٫۸- خواهد بود، در حالی که `acceleration.z` برابر ۰ و `accelerationIncludingGravity.z` برابر ۹٫۸ خواهد بود. به طور مشابه، اگر دستگاهی در حال سقوط آزاد با صفحه نمایش افقی و رو به بالا باشد، گرانش در امتداد محور Z برابر ۹٫۸- خواهد بود، در حالی که `acceleration.z` برابر ۹٫۸- و `accelerationIncludingGravity.z` برابر ۰ خواهد بود.

## مقدار

ویژگی `accelerationIncludingGravity` یک شیء حاوی اطلاعات شتاب در سه محور است. هر محور با یک ویژگی مجزا نشان داده می‌شود:

- `x`
  - : نشان‌دهنده شتاب در امتداد محور x (محور غرب به شرق)
- `y`
  - : نشان‌دهنده شتاب در امتداد محور y (محور جنوب به شمال)
- `z`
  - : نشان‌دهنده شتاب در امتداد محور z (محور پایین به بالا)

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Device orientation events/Detecting device orientation", "تشخیص جهت‌گیری دستگاه", "", "nocode")}}
- {{domxref("Device orientation events/Orientation and motion data explained", "توضیح داده‌های جهت‌گیری و حرکت", "", "nocode")}}
- رویداد {{DOMxRef("Window/devicemotion_event", "devicemotion")}}