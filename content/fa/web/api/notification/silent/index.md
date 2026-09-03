---
title: "Notification: silent property"
short-title: silent
slug: Web/API/Notification/silent
page-type: web-api-instance-property
browser-compat: api.Notification.silent
---

{{APIRef("Web Notifications")}}{{SecureContext_Header}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`silent`** در رابط {{domxref("Notification")}} مشخص می‌کند که آیا اعلان باید بی‌صدا باشد، یعنی بدون توجه به تنظیمات دستگاه، هیچ صدا یا لرزشی تولید نشود. این رفتار از طریق گزینهٔ `silent` در سازندهٔ {{domxref("Notification.Notification","Notification()")}} کنترل می‌شود.

## مقدار

یک مقدار بولین یا `null`. اگر `true` باشد، اعلان بی‌صدا است؛ اگر `null` (مقدار پیش‌فرض) باشد، تنظیمات پیش‌فرض دستگاه رعایت می‌شود.

## مثال‌ها

قطعه کد زیر یک اعلان بی‌صدا را فعال می‌کند. یک شیء `options` ساخته می‌شود و اعلان در پاسخ به کلیک دکمه با استفاده از سازندهٔ {{DOMxRef("Notification.Notification","Notification()")}} ارسال می‌شود. کد همچنین شامل مدیریت اولیهٔ مجوز است و در صورت عدم اعطای مجوز قبلی، درخواست اجازه از کاربر برای ارسال اعلان را می‌دهد.

```js
const btn = document.querySelector("button");

const options = {
  body: "No annoying pings or vibrations?",
  silent: true,
};

function requestSilentNotification() {
  const n = new Notification("Silent notification", options);
  console.log(n.silent); // should return true
}

btn.addEventListener("click", () => {
  if (Notification.permission === "granted") {
    requestSilentNotification();
  } else {
    Notification.requestPermission().then((permission) => {
      if (permission === "granted") {
        requestSilentNotification();
      } else {
        console.log("Notification permission was not granted");
      }
    });
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)