---
title: "Lock: name property"
short-title: name
slug: Web/API/Lock/name
page-type: web-api-instance-property
browser-compat: api.Lock.name
---

{{APIRef("Web Locks API")}}{{securecontext_header}} {{AvailableInWorkers}}

خاصیت فقطخواندنی **`name`** در رابط {{domxref("Lock")}}، همان _نام_ را برمیگرداند که هنگام درخواست قفل به {{domxref('LockManager.request')}} ارسال شده و برای انتخاب قفل استفاده میشود.

نام یک قفل هنگام درخواست قفل توسط اسکریپت ارسال میشود. این نام توسط توسعه‌دهنده انتخاب می‌شود تا یک منبع انتزاعی را نشان دهد که استفاده از آن بین چندین تب، worker یا کدهای دیگر در همان origin هماهنگ می‌شود. برای مثال، اگر فقط یک تب از یک برنامه وب باید منابع شبکه را با یک پایگاه‌داده آفلاین همگام‌سازی کند، می‌تواند از نام قفلی مانند `"net_db_sync"` استفاده کند.

## Value

یک رشته.

## Examples

مثال‌های زیر نشان می‌دهند که خاصیت name چگونه در فراخوانی {{domxref('LockManager.request()')}} منتقل می‌شود. {{domxref('LockManager')}} شیئی است که توسط {{domxref('navigator.locks')}} بازگردانده می‌شود.

```js
navigator.locks.request("net_db_sync", showLockProperties);

function showLockProperties(lock) {
  console.log(`The lock name is: ${lock.name}`);
  console.log(`The lock mode is: ${lock.mode}`);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}