---
title: "DeviceMotionEvent: DeviceMotionEvent() constructor"
short-title: DeviceMotionEvent()
slug: Web/API/DeviceMotionEvent/DeviceMotionEvent
page-type: web-api-constructor
browser-compat: api.DeviceMotionEvent.DeviceMotionEvent
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

سازندهٔ **`DeviceMotionEvent()`** یک شیء جدید از نوع {{DOMxRef("DeviceMotionEvent")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new DeviceMotionEvent(type)
new DeviceMotionEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است با نام رویداد. این رشته به بزرگی/کوچکی حروف حساس است و مرورگرها همیشه آن را برابر با `devicemotion` قرار می‌دهند.
- `options` {{Optional_Inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `acceleration` {{Optional_Inline}}
      - : یک {{domxref("DeviceMotionEventAcceleration")}} که شتاب دستگاه را در سه محور X، Y و Z می‌دهد. شتاب بر حسب [m/s²](https://en.wikipedia.org/wiki/Meter_per_second_squared) بیان می‌شود. اگر مشخص نشود، همهٔ ویژگی‌های داخل شیء `null` خواهند بود.
    - `accelerationIncludingGravity` {{Optional_Inline}}
      - : یک {{domxref("DeviceMotionEventAcceleration")}} که شتاب دستگاه را در سه محور X، Y و Z با تأثیر گرانش می‌دهد. شتاب بر حسب [m/s²](https://en.wikipedia.org/wiki/Meter_per_second_squared) بیان می‌شود. اگر مشخص نشود، همهٔ ویژگی‌های داخل شیء `null` خواهند بود.
    - `rotationRate` {{Optional_Inline}}
      - : یک {{domxref("DeviceMotionEventRotationRate")}} که نرخ تغییر جهت‌گیری دستگاه را در سه محور جهت‌گیری آلفا، بتا و گاما می‌دهد. نرخ چرخش بر حسب درجه بر ثانیه بیان می‌شود. اگر مشخص نشود، همهٔ ویژگی‌های داخل شیء `null` خواهند بود.
    - `interval` {{Optional_Inline}}
      - : یک عدد که بازهٔ زمانی (به میلی‌ثانیه) را نشان می‌دهد که داده‌ها از دستگاه دریافت می‌شوند. مقدار پیش‌فرض آن `0` است.

### مقدار بازگشتی

یک شیء جدید از {{domxref("DeviceMotionEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}