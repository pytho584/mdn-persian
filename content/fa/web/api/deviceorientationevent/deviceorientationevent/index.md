---
title: "DeviceOrientationEvent: DeviceOrientationEvent() constructor"
short-title: DeviceOrientationEvent()
slug: Web/API/DeviceOrientationEvent/DeviceOrientationEvent
page-type: web-api-constructor
browser-compat: api.DeviceOrientationEvent.DeviceOrientationEvent
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

سازنده **`DeviceOrientationEvent()`** یک شیء جدید از نوع {{domxref("DeviceOrientationEvent")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new DeviceOrientationEvent(type)
new DeviceOrientationEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته (string) با نام رویداد. این رشته به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `deviceorientation` یا `deviceorientationabsolute` تنظیم می‌کنند. در حالت دوم، `options.absolute` همیشه `true` است.
- `options` {{optional_inline}}
  - : یک شیء که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند دارای ویژگی‌های زیر باشد:
    - `alpha` {{optional_inline}}
      - : یک عدد که حرکت دستگاه حول محور z را نشان می‌دهد، بر حسب درجه با مقادیر بین ۰ تا ۳۶۰. مقدار پیش‌فرض `null` است.
    - `beta` {{optional_inline}}
      - : یک عدد که حرکت دستگاه حول محور x را نشان می‌دهد، بر حسب درجه با مقادیر بین ۱۸۰- تا ۱۸۰. این حرکت از جلو به عقب دستگاه را نشان می‌دهد. مقدار پیش‌فرض `null` است.
    - `gamma` {{optional_inline}}
      - : یک عدد که حرکت دستگاه حول محور y را نشان می‌دهد، بر حسب درجه با مقادیر بین ۹۰- تا ۹۰. این حرکت از چپ به راست دستگاه را نشان می‌دهد. مقدار پیش‌فرض `null` است.
    - `absolute`
      - : یک مقدار بولی (boolean) که نشان می‌دهد آیا دستگاه داده‌های جهت‌یابی را به صورت مطلق ارائه می‌دهد یا خیر. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("DeviceOrientationEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}