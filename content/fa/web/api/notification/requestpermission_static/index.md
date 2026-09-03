---
title: "Notification: requestPermission() static method"
short-title: requestPermission()
slug: Web/API/Notification/requestPermission_static
page-type: web-api-static-method
browser-compat: api.Notification.requestPermission_static
---

{{APIRef("Web Notifications")}}{{securecontext_header}}

متد ایستایی **`requestPermission()`** از رابط {{domxref("Notification")}} از کاربر برای نمایش اعلان‌ها (notifications) از مبدأ جاری (current origin) درخواست مجوز می‌کند.

این متد یک {{jsxref("Promise")}} برمی‌گرداند که با یک رشته (string) نشان‌دهندهٔ اعطا یا رد مجوز به‌انجام می‌رسد.

## Syntax

```js-nolint
Notification.requestPermission()

// Deprecated syntax using a callback
Notification.requestPermission(callback)
```

### پارامترها

- `callback` {{optional_inline}} {{deprecated_inline}}
  - : یک تابع callback اختیاری که با مقدار مجوز فراخوانی می‌شود. به نفع مقدار بازگشتی {{jsxref("Promise")}} منسوخ شده است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به رشته‌ای با مجوز انتخاب‌شده توسط کاربر تبدیل می‌شود. مقادیر ممکن برای این رشته عبارتند از:

- `granted`
  - : کاربر به‌طور صریح مجوز نمایش اعلان‌های سیستمی را برای مبدأ جاری اعطا کرده است.
- `denied`
  - : کاربر به‌طور صریح مجوز نمایش اعلان‌های سیستمی را برای مبدأ جاری رد کرده است.
- `default`
  - : تصمیم کاربر نامشخص است؛ در این حالت برنامه طوری عمل می‌کند که گویا مجوز رد شده است.

نسخهٔ منسوخ شدهٔ متد `undefined` برمی‌گرداند.

## مثال‌ها

فرض کنید این HTML ابتدایی را داریم:

```html
<button>Notify me!</button>
```

می‌توان یک اعلان را به صورت زیر ارسال کرد — در اینجا یک مجموعه کد نسبتاً مفصل و کامل ارائه می‌دهیم که می‌توانید اگر بخواهید ابتدا بررسی کنید که آیا اعلان‌ها پشتیبانی می‌شوند، سپس بررسی کنید که آیا مجوز برای مبدأ جاری برای ارسال اعلان اعطا شده است، در صورت نیاز مجوز درخواست کنید و سپس یک اعلان ارسال کنید.

توجه داشته باشید که درخواست باید در پاسخ به تعامل کاربر انجام شود: در زیر، متد درون handler رویداد کلیک فراخوانی می‌شود.

```js
document.querySelector("button").addEventListener("click", notifyMe);

function notifyMe() {
  if (!("Notification" in window)) {
    // Check if the browser supports notifications
    alert("This browser does not support desktop notification");
  } else if (Notification.permission === "granted") {
    // Check whether notification permissions have already been granted;
    // if so, create a notification
    const notification = new Notification("Hi there!");
    // …
  } else if (Notification.permission !== "denied") {
    // We need to ask the user for permission
    Notification.requestPermission().then((permission) => {
      // If the user accepts, let's create a notification
      if (permission === "granted") {
        const notification = new Notification("Hi there!");
        // …
      }
    });
  }

  // At last, if the user has denied notifications, and you
  // want to be respectful there is no need to bother them anymore.
}
```

ما دیگر یک نمونهٔ زنده در این صفحه نمایش نمی‌دهیم، زیرا Chrome و Firefox دیگر اجازه درخواست مجوز اعلان از {{htmlelement("iframe")}}های با مبدأ متفاوت (cross-origin) را نمی‌دهند و مرورگرهای دیگر نیز به همین ترتیب عمل خواهند کرد. برای مشاهده یک مثال عملی، به [مثال لیست کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید (همچنین [برنامهٔ در حال اجرا](https://mdn.github.io/dom-examples/to-do-notifications/) را ببینید).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)