---
title: "GeolocationCoordinates: heading property"
short-title: heading
slug: Web/API/GeolocationCoordinates/heading
page-type: web-api-instance-property
browser-compat: api.GeolocationCoordinates.heading
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

ویژگی فقط‌خواندنی **`heading`** در رابط {{domxref("GeolocationCoordinates")}} یک `double` است که جهتی را نشان می‌دهد که دستگاه در آن در حال حرکت است. این مقدار، که بر حسب درجه بیان می‌شود، میزان انحراف دستگاه از جهت شمال حقیقی را مشخص می‌کند. `0` درجه نمایانگر شمال حقیقی است و جهت به‌صورت ساعت‌گرد تعیین می‌شود (به این معنی که شرق `90` درجه و غرب `270` درجه است). اگر {{domxref("GeolocationCoordinates.speed")}} برابر `0` باشد یا دستگاه نتواند اطلاعات جهت را فراهم کند، `heading` برابر `null` خواهد بود.

## مقدار

یک `double` که جهت حرکت دستگاه را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("GeolocationCoordinates")}}