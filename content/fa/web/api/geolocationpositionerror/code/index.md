---
title: "GeolocationPositionError: code property"
short-title: code
slug: Web/API/GeolocationPositionError/code
page-type: web-api-instance-property
browser-compat: api.GeolocationPositionError.code
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

ویژگی فقط‌خواندنی **`code`** در رابط {{domxref("GeolocationPositionError")}} یک `unsigned short` است که کد خطا را نشان می‌دهد.

مقادیر زیر امکان‌پذیر هستند:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">مقدار</th>
      <th scope="col">ثابت مرتبط</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>1</code></td>
      <td><code>PERMISSION_DENIED</code></td>
      <td>
        دریافت اطلاعات موقعیت مکانی به این دلیل که صفحه مجوز انجام آن را نداشت، ناموفق بود.
      </td>
    </tr>
    <tr>
      <td><code>2</code></td>
      <td><code>POSITION_UNAVAILABLE</code></td>
      <td>
        دریافت اطلاعات موقعیت مکانی به دلیل بازگشت یک خطای داخلی از یک یا چند منبع داخلی موقعیت، ناموفق بود.
      </td>
    </tr>
    <tr>
      <td><code>3</code></td>
      <td><code>TIMEOUT</code></td>
      <td>اطلاعات موقعیت مکانی در مدت زمان مجاز به دست نیامد.</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از geolocation](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("GeolocationPositionError")}}