---
title: "DeviceMotionEvent: rotationRate property"
---

---
title: "DeviceMotionEvent: rotationRate property"
short-title: rotationRate
slug: Web/API/DeviceMotionEvent/rotationRate
page-type: web-api-instance-property
browser-compat: api.DeviceMotionEvent.rotationRate
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`rotationRate`** در رابط {{domxref("DeviceMotionEvent")}} نرخ چرخش دستگاه به دور هر یک از محورهای آن را بر حسب درجه بر ثانیه برمی‌گرداند.

> [!NOTE]
> اگر سخت‌افزار قادر به ارائه این اطلاعات نباشد، این ویژگی مقدار `null` برمی‌گرداند.

## Value

ویژگی `rotationRate` یک شیء فقط‌خواندنی است که نرخ چرخش دستگاه به دور هر یک از محورهای آن را توصیف می‌کند:

- `alpha`
  - : نرخی که دستگاه به دور محور X خود می‌چرخد؛ یعنی از جلو به عقب.
- `beta`
  - : نرخی که دستگاه به دور محور Y خود می‌چرخد؛ یعنی از یک سمت به سمت دیگر.
- `gamma`
  - : نرخی که دستگاه به دور محور Z خود می‌چرخد؛ یعنی چرخش حول خطی عمود بر صفحه نمایش.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Device orientation events/Detecting device orientation", "Detecting device orientation", "", "nocode")}}
- {{domxref("Device orientation events/Orientation and motion data explained", "Orientation and motion data explained", "", "nocode")}}
- {{DOMxRef("Window/devicemotion_event", "devicemotion")}} event