---
title: "Notification: dir property"
short-title: dir
slug: Web/API/Notification/dir
page-type: web-api-instance-property
browser-compat: api.Notification.dir
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

خاصیت فقط خواندنی **`dir`** از رابط {{domxref("Notification")}} جهت متن اعلان را نشان می‌دهد، همانطور که در گزینه `dir` سازنده {{domxref("Notification.Notification","Notification()")}} مشخص شده است.

## مقدار

یک رشته که جهت متن را مشخص می‌کند. مقادیر ممکن عبارتند از:

- `auto`
  - : رفتار تنظیمات زبان مرورگر را اتخاذ می‌کند (پیش‌فرض).
- `ltr`
  - : چپ به راست.
- `rtl`
  - : راست به چپ.

> [!NOTE]
> به نظر می‌رسد بیشتر مرورگرها تنظیمات صریح `ltr` و `rtl` را نادیده می‌گیرند و فقط از تنظیمات سراسری مرورگر پیروی می‌کنند.

## مثال‌ها

قطعه کد زیر یک اعلان را ایجاد می‌کند؛ یک شیء ساده `options` ساخته شده و سپس اعلان با استفاده از سازنده `Notification()` ایجاد می‌شود.

```js
const options = {
  body: "Your code submission has received 3 new review comments.",
  dir: "rtl",
};

const n = new Notification("New review activity", options);

console.log(n.dir); // "rtl"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)