---
title: "Lock"
slug: Web/API/Lock
page-type: web-api-interface
browser-compat: api.Lock
---
{{APIRef("Web Locks API")}}{{securecontext_header}} {{AvailableInWorkers}}

رابط **`Lock`** از [Web Locks API](/en-US/docs/Web/API/Web_Locks_API) نام و حالت یک قفل را ارائه می‌دهد. این می‌تواند یک قفل تازه‌درخواست‌شده باشد که در callback به {{domxref('LockManager.request','LockManager.request()')}} دریافت می‌شود، یا یک رکورد از یک قفل فعال یا در صف که توسط {{domxref('LockManager.query()')}} بازگردانده می‌شود.

## ویژگی‌های نمونه

- {{domxref('Lock.mode')}} {{ReadOnlyInline}}
  - : حالت دسترسی که در هنگام درخواست قفل به {{domxref('LockManager.request()')}} ارسال شده را برمی‌گرداند. حالت یا `"exclusive"` (پیش‌فرض) است یا `"shared"`.
- {{domxref('Lock.name')}} {{ReadOnlyInline}}
  - : نامی که در هنگام درخواست قفل به {{domxref('LockManager.request()')}} ارسال شده را برمی‌گرداند.

## مثال‌ها

مثال‌های زیر نشان می‌دهند که چگونه ویژگی‌های `mode` و `name` در فراخوانی {{domxref('LockManager.request()')}} ارسال می‌شوند. {{domxref('LockManager')}} شیئی است که توسط {{domxref('navigator.locks')}} بازگردانده می‌شود.

```js
navigator.locks.request("net_db_sync", showLockProperties);
navigator.locks.request("another_lock", { mode: "shared" }, showLockProperties);

function showLockProperties(lock) {
  console.log(`The lock name is: ${lock.name}`);
  console.log(`The lock mode is: ${lock.mode}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}