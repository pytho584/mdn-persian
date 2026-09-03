---
title: "Notification: title property"
short-title: title
slug: Web/API/Notification/title
page-type: web-api-instance-property
browser-compat: api.Notification.title
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`title`** در رابط {{domxref("Notification")}} عنوان اعلان را نشان می‌دهد، همان‌طور که در پارامتر `title` سازندهٔ {{domxref("Notification.Notification","Notification()")}} مشخص شده است.

## مقدار

یک رشته.

## مثال‌ها

```js
function spawnNotification(theBody, theIcon, theTitle) {
  const options = {
    body: theBody,
    icon: theIcon,
  };

  const n = new Notification(theTitle, options);

  console.log(n.title);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)