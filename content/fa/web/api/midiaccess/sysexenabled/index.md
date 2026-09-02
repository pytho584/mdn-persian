---
title: "MIDIAccess: sysexEnabled property"
short-title: sysexEnabled
slug: Web/API/MIDIAccess/sysexEnabled
page-type: web-api-instance-property
browser-compat: api.MIDIAccess.sysexEnabled
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

خاصیتِ فقط‌خواندنی **`sysexEnabled`** در رابط {{domxref("MIDIAccess")}} مشخص می‌کند که آیا پشتیبانی از System Exclusive (اختصاصی سیستم) در نمونهٔ فعلی `MIDIAccess` فعال است یا خیر.

## مقدار

یک مقدار بولی (boolean).

## مثال‌ها

متد {{domxref("Navigator.requestMIDIAccess()")}} یک Promise برمی‌گرداند که با یک شیء {{domxref("MIDIAccess")}} حل می‌شود. چاپ مقدار `sysexEnabled` در کنسول، یک مقدار بولی برمی‌گرداند که اگر پشتیبانی System Exclusive فعال باشد، `true` خواهد بود.

```js
navigator.requestMIDIAccess().then((access) => {
  console.log(access.sysexEnabled);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}