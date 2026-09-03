---
title: "Notification: lang property"
short-title: lang
slug: Web/API/Notification/lang
page-type: web-api-instance-property
browser-compat: api.Notification.lang
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lang`** از رابط {{domxref("Notification")}} نشان‌دهندهٔ زبانی است که در اعلان استفاده شده است، همان‌طور که در گزینهٔ `lang` سازندهٔ {{domxref("Notification.Notification","Notification()")}} مشخص شده است.

زبان با استفاده از یک رشته که نشان‌دهندهٔ یک {{glossary("BCP 47 language tag")}} است مشخص می‌شود.

## مقدار

یک رشته که برچسب زبان را مشخص می‌کند.

## مثال‌ها

قطعه کد زیر یک اعلان را راه‌اندازی می‌کند؛ یک شیء ساده `options` ساخته شده و سپس اعلان با استفاده از سازندهٔ `Notification()` راه‌اندازی می‌شود.

```js
const options = {
  body: "Your code submission has received 3 new review comments.",
  lang: "en-US",
};

const n = new Notification("New review activity", options);

console.log(n.lang); // "en-US"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)