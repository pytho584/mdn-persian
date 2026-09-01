---
title: "Geolocation: clearWatch() method"
short-title: clearWatch()
slug: Web/API/Geolocation/clearWatch
page-type: web-api-instance-method
browser-compat: api.Geolocation.clearWatch
---

{{securecontext_header}}{{ APIref("Geolocation API") }}

متد **`clearWatch()`** در رابط {{domxref("Geolocation")}} برای لغو نظارت‌هایی که قبلاً با استفاده از {{domxref("Geolocation.watchPosition()")}} برای موقعیت/خطا ثبت شده‌اند، به کار می‌رود.

## نحو (Syntax)

```js-nolint
clearWatch(id)
```

### پارامترها

- `id`
  - : شماره شناسایی که توسط متد {{domxref("Geolocation.watchPosition()")}} هنگام نصبِ نظارت‌کننده‌ای که می‌خواهید حذف کنید، بازگردانده شده است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
let id;
let target;
let options;

function success(pos) {
  const crd = pos.coords;

  if (target.latitude === crd.latitude && target.longitude === crd.longitude) {
    console.log("Congratulations, you've reached the target!");
    navigator.geolocation.clearWatch(id);
  }
}

function error(err) {
  console.error(`ERROR(${err.code}): ${err.message}`);
}

target = {
  latitude: 0,
  longitude: 0,
};

options = {
  enableHighAccuracy: false,
  timeout: 5000,
  maximumAge: 0,
};

id = navigator.geolocation.watchPosition(success, error, options);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از موقعیت‌یابی جغرافیایی](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("Geolocation")}}
- {{domxref("Geolocation.watchPosition()")}}
- {{domxref("Geolocation.getCurrentPosition()")}}