---
title: "Notification: renotify property"
short-title: renotify
slug: Web/API/Notification/renotify
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Notification.renotify
---

{{APIRef("Web Notifications")}}{{SecureContext_Header}}{{SeeCompatTable}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`renotify`** در رابط {{domxref("Notification")}} مشخص می‌کند که آیا کاربر باید پس از جایگزینی یک اعلان قدیمی با اعلان جدید، دوباره مطلع شود یا خیر. این رفتار با گزینه `renotify` در سازنده {{domxref("Notification.Notification","Notification()")}} تعیین می‌شود.

## مقدار

یک مقدار بولی. مقدار پیش‌فرض `false` است؛ `true` باعث می‌شود که اعلان دوباره کاربر را مطلع کند.

## مثال‌ها

قطعه کد زیر یک اعلان ایجاد می‌کند که پس از جایگزینی، دوباره کاربر را مطلع می‌کند؛ یک شیء ساده `options` ساخته می‌شود و سپس اعلان با استفاده از سازنده `Notification()` فرستاده می‌شود.

```js
const options = {
  body: "Your code submission has received 3 new review comments.",
  renotify: true,
};

const n = new Notification("New review activity", options);

console.log(n.renotify); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)