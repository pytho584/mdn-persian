---
title: "GravitySensor: GravitySensor() constructor"
---

---
title: "GravitySensor: GravitySensor() constructor"
short-title: GravitySensor()
slug: Web/API/GravitySensor/GravitySensor
page-type: web-api-constructor
browser-compat: api.GravitySensor.GravitySensor
---

{{securecontext_header}}{{APIRef("Sensor API")}}

سازندهٔ **`GravitySensor()`** یک شیء {{domxref("GravitySensor")}} جدید می‌سازد که در هر بار خواندن، گرانش وارد بر دستگاه را در هر سه محور فراهم می‌کند.

## Syntax

```js-nolint
new GravitySensor()
new GravitySensor(options)
```

### Parameters

- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند:
    - `frequency` {{optional_inline}}
      - : تعداد بارهای مورد نظر در هر ثانیه برای نمونه‌برداری، یعنی تعداد باری که رویداد {{domxref('sensor.reading_event', 'reading')}} در هر ثانیه فراخوانی می‌شود. می‌توان از یک عدد صحیح یا اعشاری استفاده کرد؛ عدد اعشاری برای فرکانس‌های کمتر از یک ثانیه. فرکانس واقعی خواندن به سخت‌افزار دستگاه بستگی دارد و در نتیجه ممکن است کمتر از مقدار درخواستی باشد. فرکانس پیش‌فرض، فرکانسی است که توسط پلتفرم زیرین تعریف شده است.
    - `referenceFrame` {{optional_inline}}
      - : سیستم مختصات محلی که چارچوب مرجع را نشان می‌دهد. این مقدار می‌تواند `'device'` یا `'screen'` باشد. پیش‌فرض `'device'` است.

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref('sensor.reading_event', 'reading')}} رویداد