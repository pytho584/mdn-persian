---
title: "MediaKeySession: keystatuseschange event"
short-title: keystatuseschange
slug: Web/API/MediaKeySession/keystatuseschange_event
page-type: web-api-event
browser-compat: api.MediaKeySession.keystatuseschange_event
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

رویداد **`keystatuseschange`** از API شیء {{domxref("MediaKeySession")}} هنگامی رخ می‌دهد که تغییری در کلیدها یا وضعیت‌های آن‌ها در یک نشست (session) ایجاد شده باشد.

## سینتکس

برای گوش دادن به این رویداد، نام رویداد را در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کنندهٔ رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("keystatuseschange", (event) => { })

onkeystatuseschange = (event) => { }
```

## نوع رویداد

یک {{domxref("ExtendableEvent")}} که از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("ExtendableEvent")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}