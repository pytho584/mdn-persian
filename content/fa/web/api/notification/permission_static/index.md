---
title: "Notification: permission static property"
short-title: permission
slug: Web/API/Notification/permission_static
page-type: web-api-static-property
browser-compat: api.Notification.permission_static
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

خاصیت ایستا و فقط‑خواندنی **`permission`** در رابط {{domxref("Notification")}} مجوز فعلی اعطاشده توسط کاربر برای نمایش اعلان‌های وب در مبدأ (origin) جاری را نشان می‌دهد.

## مقدار

یک رشته که مجوز فعلی را نمایش می‌دهد. مقدار می‌تواند یکی از موارد زیر باشد:

- `granted`
  - : کاربر به‌طور صریح برای نمایش اعلان‌های سیستمی از مبدأ جاری مجوز داده است.
- `denied`
  - : کاربر به‌طور صریح از نمایش اعلان‌های سیستمی از مبدأ جاری خودداری کرده است.
- `default`
  - : تصمیم کاربر نامشخص است؛ در این حالت برنامه طوری عمل می‌کند که گویی مجوز رد شده است (`denied`).

## مثال‌ها

قطعه کد زیر می‌تواند برای بررسی اینکه آیا اعلان‌ها پشتیبانی می‌شوند، سپس بررسی اینکه آیا مجوز ارسال اعلان از مبدأ جاری داده شده است، و در صورت نیاز درخواست مجوز قبل از ارسال اعلان، استفاده شود.

```js
function notifyMe() {
  if (!("Notification" in window)) {
    // بررسی اینکه آیا مرورگر از اعلان‌ها پشتیبانی می‌کند
    alert("این مرورگر از اعلان دسکتاپ پشتیبانی نمی‌کند");
  } else if (Notification.permission === "granted") {
    // بررسی اینکه آیا مجوز اعلان قبلاً داده شده است؛
    // اگر بله، یک اعلان ایجاد کنید
    const notification = new Notification("سلام!");
    // …
  } else if (Notification.permission !== "denied") {
    // باید از کاربر مجوز بخواهیم
    Notification.requestPermission().then((permission) => {
      // اگر کاربر پذیرفت، یک اعلان ایجاد کنیم
      if (permission === "granted") {
        const notification = new Notification("سلام!");
        // …
      }
    });
  }

  // در نهایت، اگر کاربر اعلان‌ها را رد کرده است و شما می‌خواهید
  // محترمانه رفتار کنید، نیازی به اذیت کردن دوباره او نیست.
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Notifications API](/en-US/docs/Web/API/Notifications_API)
- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)
- [Permissions API](/en-US/docs/Web/API/Permissions_API)
- [استفاده از Permissions API](/en-US/docs/Web/API/Permissions_API/Using_the_Permissions_API)