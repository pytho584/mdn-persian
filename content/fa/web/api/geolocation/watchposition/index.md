---
title: "Geolocation: watchPosition() method"
short-title: watchPosition()
slug: Web/API/Geolocation/watchPosition
page-type: web-api-instance-method
browser-compat: api.Geolocation.watchPosition
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

متد **`watchPosition()`** از رابط {{domxref("Geolocation")}} برای ثبت یک تابع handler استفاده می‌شود که هر بار موقعیت دستگاه تغییر کند، به‌طور خودکار فراخوانی می‌شود.
همچنین می‌توانید به صورت اختیاری یک تابع callback برای مدیریت خطا مشخص کنید.

توجه داشته باشید که علاوه بر نیاز به زمینه امن (secure context)، این قابلیت ممکن است توسط [`geolocation`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/geolocation) از طریق `Permissions-Policy` مسدود شود و همچنین نیاز به اجازه صریح کاربر دارد.
در صورت نیاز، هنگام فراخوانی این متد از کاربر درخواست مجوز می‌شود.
وضعیت مجوز را می‌توان با استفاده از مجوز کاربر `geolocation` در [Permissions API](/en-US/docs/Web/API/Permissions_API) پرس‌وجو کرد.

## نحو (Syntax)

```js-nolint
watchPosition(success)
watchPosition(success, error)
watchPosition(success, error, options)
```

### پارامترها

- `success`
  - : یک تابع callback که یک شیء {{domxref("GeolocationPosition")}} را به عنوان پارامتر ورودی دریافت می‌کند.
- `error` {{optional_inline}}
  - : یک تابع callback اختیاری که یک شیء {{domxref("GeolocationPositionError")}} را به عنوان پارامتر ورودی دریافت می‌کند.
- `options` {{optional_inline}}
  - : یک شیء اختیاری که گزینه‌های پیکربندی برای نظارت بر موقعیت را فراهم می‌کند.
    برای جزئیات بیشتر درباره گزینه‌های ممکن به {{domxref("Geolocation.getCurrentPosition()")}} مراجعه کنید.

### مقدار بازگشتی

یک شناسه عددی (integer ID) که handler ثبت‌شده را مشخص می‌کند.
این شناسه را می‌توان به {{domxref("Geolocation.clearWatch()")}} ارسال کرد تا handler لغو ثبت شود.

## مثال‌ها

```js
let id;
let target;
let options;

function success(pos) {
  const crd = pos.coords;

  if (target.latitude === crd.latitude && target.longitude === crd.longitude) {
    console.log("Congratulations, you reached the target");
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

- [استفاده از API موقعیت‌یابی (Geolocation API)](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- رابطی که به آن تعلق دارد، {{domxref("Geolocation")}}، و روش دسترسی به آن —
  {{domxref("Navigator.geolocation")}}.
- عملیات مخالف: {{domxref("Geolocation.clearWatch()")}}
- یک روش مشابه: {{domxref("Geolocation.getCurrentPosition()")}}