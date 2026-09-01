---
title: "DeviceOrientationEvent: absolute property"
---

---
title: "DeviceOrientationEvent: absolute property"
short-title: absolute
slug: Web/API/DeviceOrientationEvent/absolute
page-type: web-api-instance-property
browser-compat: api.DeviceOrientationEvent.absolute
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`absolute`** در رابط {{domxref("DeviceOrientationEvent")}} نشان می‌دهد که آیا دستگاه داده‌های جهت‌گیری را به‌صورت مطلق (یعنی با مرجع چارچوب مختصات زمین) ارائه می‌کند یا از یک چارچوب دلخواه که توسط خود دستگاه تعیین شده استفاده می‌کند. برای جزئیات بیشتر، [توضیح جهت‌گیری و داده‌های حرکت](/en-US/docs/Web/API/Device_orientation_events/Orientation_and_motion_data_explained) را ببینید.

## مقدار

- اگر در `instanceOfDeviceOrientationEvent` داده‌های جهت‌گیری به‌صورت اختلاف بین چارچوب مختصات زمین و چارچوب مختصات دستگاه ارائه شده باشد، مقدار `true` برمی‌گردد.
- اگر داده‌های جهت‌گیری با مرجع یک چارچوب مختصات دلخواه و تعیین‌شده توسط دستگاه ارائه شده باشند، مقدار `false` برمی‌گردد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Device orientation events/Detecting device orientation", "Detecting device orientation", "", "nocode")}}
- {{domxref("Device orientation events/Orientation and motion data explained", "Orientation and motion data explained", "", "nocode")}}
- رویداد {{domxref("Window.deviceorientation_event", "deviceorientation")}}
- رویداد {{domxref("Window.deviceorientationabsolute_event", "deviceorientationabsolute")}}