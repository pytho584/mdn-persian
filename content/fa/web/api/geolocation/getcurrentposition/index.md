---
title: "Geolocation: getCurrentPosition() method"
---

---
title: "Geolocation: getCurrentPosition() method"
short-title: getCurrentPosition()
slug: Web/API/Geolocation/getCurrentPosition
page-type: web-api-instance-method
browser-compat: api.Geolocation.getCurrentPosition
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

متد **`getCurrentPosition()`** از رابط {{domxref("Geolocation")}} برای دریافت موقعیت فعلی دستگاه استفاده می‌شود.

توجه داشته باشید که علاوه بر نیاز به زمینهٔ امن (secure context)، این قابلیت ممکن است توسط [`geolocation`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/geolocation) از نوع `Permissions-Policy` مسدود شود و همچنین به اجازهٔ صریح کاربر نیاز دارد. در صورت لزوم، هنگام فراخوانی این متد از کاربر درخواست مجوز می‌شود. وضعیت مجوز را می‌توان با استفاده از مجوز کاربر `geolocation` در [Permissions API](/en-US/docs/Web/API/Permissions_API) پرس‌وجو کرد.

## Syntax

```js-nolint
getCurrentPosition(success)
getCurrentPosition(success, error)
getCurrentPosition(success, error, options)
```

### Parameters

- `success`
  - : یک تابع callback که یک شیء {{domxref("GeolocationPosition")}} را به‌عنوان تنها ورودی خود دریافت می‌کند.
- `error` {{optional_inline}}
  - : یک تابع callback اختیاری که یک شیء {{domxref("GeolocationPositionError")}} را به‌عنوان تنها ورودی خود دریافت می‌کند.
- `options` {{optional_inline}}
  - : یک شیء اختیاری شامل پارامترهای زیر:
    - `maximumAge` {{optional_inline}}
      - : یک مقدار `long` مثبت که حداکثر سن (به میلی‌ثانیه) یک موقعیت ذخیره‌شده (cached) را تعیین می‌کند که بازگرداندن آن قابل قبول است. اگر روی `0` تنظیم شود، به این معنی است که دستگاه نمی‌تواند از موقعیت ذخیره‌شده استفاده کند و باید تلاش کند موقعیت واقعی فعلی را بازیابی کند. اگر روی {{jsxref("Infinity")}} تنظیم شود، دستگاه باید بدون توجه به سن موقعیت، موقعیت ذخیره‌شده را بازگرداند. مقدار پیش‌فرض: `0`.
    - `timeout` {{optional_inline}}
      - : یک مقدار `long` مثبت که حداکثر زمان مجاز (به میلی‌ثانیه) برای بازگرداندن موقعیت توسط دستگاه را نشان می‌دهد. مقدار پیش‌فرض {{jsxref("Infinity")}} است، به این معنی که `getCurrentPosition()` تا زمانی که موقعیت در دسترس نباشد، بازنمی‌گردد.
    - `enableHighAccuracy` {{optional_inline}}
      - : یک مقدار بولین (boolean) که نشان می‌دهد برنامه مایل است بهترین نتایج ممکن را دریافت کند. اگر `true` باشد و دستگاه بتواند موقعیت دقیق‌تری ارائه دهد، این کار را انجام می‌دهد. توجه داشته باشید که این امر می‌تواند به زمان پاسخ‌دهی کندتر یا مصرف انرژی بیشتر منجر شود (مثلاً با تراشه GPS در دستگاه همراه). از سوی دیگر، اگر `false` باشد، دستگاه می‌تواند با پاسخ‌دهی سریع‌تر و/یا مصرف توان کمتر، منابع را ذخیره کند. مقدار پیش‌فرض: `false`.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

```js
const options = {
  enableHighAccuracy: true,
  timeout: 5000,
  maximumAge: 0,
};

function success(pos) {
  const crd = pos.coords;

  console.log("Your current position is:");
  console.log(`Latitude: ${crd.latitude}`);
  console.log(`Longitude: ${crd.longitude}`);
  console.log(`More or less ${crd.accuracy} meters.`);
}

function error(err) {
  console.warn(`ERROR(${err.code}): ${err.message}`);
}

navigator.geolocation.getCurrentPosition(success, error, options);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("Navigator.geolocation")}}