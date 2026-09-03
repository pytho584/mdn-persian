---
title: "Notification: vibrate property"
short-title: vibrate
slug: Web/API/Notification/vibrate
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Notification.vibrate
---

{{APIRef("Web Notifications")}}{{SecureContext_Header}}{{SeeCompatTable}} {{AvailableInWorkers}}

ویژگی **`vibrate`** با وضعیت فقط‌خواندنی از رابط {{domxref("Notification")}} یک [الگوی لرزش](/en-US/docs/Web/API/Vibration_API#vibration_patterns) را برای سخت‌افزار لرزش دستگاه مشخص می‌کند که هنگام فعال‌شدن اعلان باید منتشر شود. این مقدار از طریق گزینهٔ `vibrate` در سازندهٔ {{domxref("Notification.Notification","Notification()")}} تعیین می‌شود.

## مقدار

یک [الگوی لرزش](/en-US/docs/Web/API/Vibration_API#vibration_patterns)، همان‌طور که در [مشخصات Vibration API](https://w3c.github.io/vibration/) مشخص شده است.

## مثال‌ها

قطعه‌کد زیر برای ایجاد اعلانی در نظر گرفته شده است که لرزش دستگاه را نیز فعال می‌کند؛ یک شیء ساده به نام `options` ساخته می‌شود و سپس اعلان با استفاده از سازندهٔ `Notification()` فعال می‌شود.

```js
const options = {
  body: "Your code submission has received 3 new review comments.",
  vibrate: [200, 100, 200],
};

const n = new Notification("New review activity", options);

console.log(n.vibrate); // [200, 100, 200]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)