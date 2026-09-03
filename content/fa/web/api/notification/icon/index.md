---
title: "Notification: icon property"
short-title: icon
slug: Web/API/Notification/icon
page-type: web-api-instance-property
browser-compat: api.Notification.icon
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`icon`** در رابط {{domxref("Notification")}} حاوی URL آیکنی است که به‌عنوان بخشی از اعلان نمایش داده می‌شود؛ همان‌طور که در گزینه `icon` سازنده {{domxref("Notification.Notification","Notification()")}} مشخص شده است.

## مقدار

یک رشته (string).

## مثال‌ها

در [برنامه فهرست کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما ([مشاهده اجرای زنده برنامه](https://mdn.github.io/dom-examples/to-do-notifications/))، از سازنده {{domxref("Notification.Notification","Notification()")}} برای ایجاد یک اعلان استفاده می‌کنیم و آرگومان‌هایی برای مشخص کردن متن، آیکن و عنوان موردنظر به آن می‌دهیم.

```js
const notification = new Notification("To do list", {
  body: text,
  icon: img,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)