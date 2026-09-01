---
title: "HTMLMediaElement: remote property"
short-title: remote
slug: Web/API/HTMLMediaElement/remote
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.remote
---

{{APIRef("Remote Playback API")}}

ویژگی فقط‌خواندنی **`remote`** در رابط {{domxref("HTMLMediaElement")}}، شیء {{domxref("RemotePlayback")}} مرتبط با عنصر رسانه‌ای را برمی‌گرداند. شیء `RemotePlayback` امکان کنترل دستگاه‌های راه‌دور را که در حال پخش رسانه هستند فراهم می‌کند.

## مقدار

یک شیء {{domxref("RemotePlayback")}} مرتبط با عنصر رسانه‌ای.

## مثال

```js
const el = document.createElement("audio");
const remotePlayback = el.remote;

remotePlayback.watchAvailability((availability) => {
  // Do something when the availability changes
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}