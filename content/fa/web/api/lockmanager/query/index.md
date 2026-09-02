---
title: "LockManager: query() method"
short-title: query()
slug: Web/API/LockManager/query
page-type: web-api-instance-method
browser-compat: api.LockManager.query
---

{{APIRef("Web Locks API")}}{{securecontext_header}} {{AvailableInWorkers}}

متد **`query()`** از رابط {{domxref("LockManager")}} یک {{jsxref('Promise')}} برمی‌گرداند که با یک شیء شامل اطلاعات مربوط به قفل‌های نگه‌داری‌شده و قفل‌های در انتظار resolve می‌شود.

## سینتکس

```js-nolint
query()
```

### پارامترها

هیچ پارامتری ندارد.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که با یک شیء resolve می‌شود و شامل تصویری آنی (snapshot) از وضعیت {{domxref("LockManager")}} است. این شیء ویژگی‌های زیر را دارد:

- `held`
  - : آرایه‌ای از اشیاء `LockInfo` برای قفل‌های نگه‌داری‌شده.
- `pending`
  - : آرایه‌ای از اشیاء `LockInfo` برای درخواست‌های قفل در انتظار.

شیء `LockInfo` می‌تواند ویژگی‌های زیر را داشته باشد:

- `name`
  - : نامی که هنگام درخواست قفل به {{domxref("LockManager.request()")}} ارسال شده است.
- `mode`
  - : حالت دسترسی که هنگام درخواست قفل به {{domxref("LockManager.request()")}} ارسال شده است. این حالت یا `"exclusive"` است یا `"shared"`.
- `clientId`
  - : هویت یکتای زمینه‌ای که {{domxref("LockManager.request()")}} در آن فراخوانی می‌شود. این مقدار با {{domxref("Client.id")}} یکسان است.

### استثناها

ممکن است این متد یک promise برگرداند که با یک {{domxref("DOMException")}} از یکی از انواع زیر رد شده باشد:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سندِ محیط به‌طور کامل فعال نباشد، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر نتوان برای محیط جاری یک مدیر قفل (lock manager) به دست آورد، پرتاب می‌شود.

## مثال‌ها

```js
const state = await navigator.locks.query();
for (const lock of state.held) {
  console.log(`held lock: name ${lock.name}, mode ${lock.mode}`);
}
for (const request of state.pending) {
  console.log(`requested lock: name ${request.name}, mode ${request.mode}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}