---
title: "GeolocationCoordinates"
---

---
title: GeolocationCoordinates
slug: Web/API/GeolocationCoordinates
page-type: web-api-interface
browser-compat: api.GeolocationCoordinates
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

واسط **`GeolocationCoordinates`** موقعیت و ارتفاع دستگاه روی زمین را به همراه دقت محاسبه این ویژگی‌ها نشان می‌دهد. اطلاعات موقعیت جغرافیایی بر اساس مختصات سیستم ژئودتیک جهانی (WGS84) ارائه می‌شود.

## ویژگی‌های نمونه

_واسط `GeolocationCoordinates` هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("GeolocationCoordinates.latitude")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که عرض جغرافیایی موقعیت را بر حسب درجه اعشاری نشان می‌دهد.
- {{domxref("GeolocationCoordinates.longitude")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که طول جغرافیایی موقعیت را بر حسب درجه اعشاری نشان می‌دهد.
- {{domxref("GeolocationCoordinates.altitude")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که ارتفاع موقعیت را بر حسب متر، نسبت به سطح متوسط آب‌های آزاد نشان می‌دهد. اگر پیاده‌سازی نتواند این داده را فراهم کند، مقدار آن می‌تواند `null` باشد.
- {{domxref("GeolocationCoordinates.accuracy")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که دقت ویژگی‌های `latitude` و `longitude` را بر حسب متر نشان می‌دهد.
- {{domxref("GeolocationCoordinates.altitudeAccuracy")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که دقت مقدار `altitude` را بر حسب متر نشان می‌دهد. اگر پیاده‌سازی نتواند این داده را فراهم کند، مقدار آن می‌تواند `null` باشد.
- {{domxref("GeolocationCoordinates.heading")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که جهت رو به روی دستگاه را نشان می‌دهد. این مقدار که بر حسب درجه مشخص می‌شود، میزان انحراف دستگاه از شمال حقیقی را نشان می‌دهد. `0` درجه به معنای شمال حقیقی است و جهت به صورت ساعتگرد تعیین می‌شود (یعنی شرق `90` درجه و غرب `270` درجه است). اگر مقدار `speed` صفر باشد یا دستگاه نتواند اطلاعات `heading` را ارائه دهد، مقدار `heading` برابر `null` خواهد بود.
- {{domxref("GeolocationCoordinates.speed")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند که سرعت دستگاه را بر حسب متر بر ثانیه نشان می‌دهد. این مقدار می‌تواند `null` باشد.

## روش‌های نمونه

_واسط `GeolocationCoordinates` هیچ روشی را به ارث نمی‌برد._

- {{domxref("GeolocationCoordinates.toJSON()")}}
  - : یک نمایش JSON از شیء `GeolocationCoordinates` برمی‌گرداند و سریال‌سازی را با {{jsxref("JSON.stringify()")}} فعال می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API موقعیت‌یابی](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("Geolocation")}}