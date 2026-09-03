---
title: "PermissionStatus: change event"
short-title: change
slug: Web/API/PermissionStatus/change_event
page-type: web-api-event
browser-compat: api.PermissionStatus.change_event
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}

رویداد **`change`** از رابط {{domxref("PermissionStatus")}} هر زمان که خاصیت {{domxref("PermissionStatus.state")}} تغییر کند، رخ می‌دهد.

## سینتکس

نام این رویداد را می‌توانید در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی مدیریت رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

```js
navigator.permissions
  .query({ name: "geolocation" })
  .then((permissionStatus) => {
    console.log(`geolocation permission state is ${permissionStatus.state}`);
    permissionStatus.onchange = () => {
      console.log(
        `geolocation permission state has changed to ${permissionStatus.state}`,
      );
    };
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}