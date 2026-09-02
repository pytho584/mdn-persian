---
title: "Lock: mode property"
short-title: mode
slug: Web/API/Lock/mode
page-type: web-api-instance-property
browser-compat: api.Lock.mode
---

{{APIRef("Web Locks API")}}{{securecontext_header}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`mode`** در رابط {{domxref("Lock")}}، حالت دسترسی‌ای را برمی‌گرداند که هنگام درخواست قفل، به {{domxref('LockManager.request()')}} ارسال شده است. این حالت یا `"exclusive"` است (پیش‌فرض) یا `"shared"`.

## مقدار

یکی از مقادیر `"exclusive"` یا `"shared"`.

## مثال‌ها

نمونه‌های زیر نشان می‌دهند که ویژگی mode چگونه در فراخوانی {{domxref('LockManager.request()')}} ارسال می‌شود.
{{domxref('LockManager')}} شیءای است که توسط {{domxref('navigator.locks')}} بازگردانده می‌شود.

```js
// باید "exclusive" نمایش دهد (پیش‌فرض)
navigator.locks.request("my_resource", showLockProperties);

// باید "exclusive" نمایش دهد
navigator.locks.request(
  "my_resource",
  { mode: "exclusive" },
  showLockProperties,
);

// باید "shared" نمایش دهد
navigator.locks.request("my_resource", { mode: "shared" }, showLockProperties);

function showLockProperties(lock) {
  console.log(`The lock name is: ${lock.name}`);
  console.log(`The lock mode is: ${lock.mode}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}