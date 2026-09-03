---
title: "Notification: body property"
short-title: body
slug: Web/API/Notification/body
page-type: web-api-instance-property
browser-compat: api.Notification.body
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

ویژگی فقطخواندنی **`body`** در رابط {{domxref("Notification")}}، رشته‌ای است که متن اعلان را نشان می‌دهد؛ همان رشته‌ای که در گزینهٔ `body` در سازندهٔ {{domxref("Notification.Notification","Notification()")}} تعیین می‌شود.

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

  console.log(n.body);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)