---
title: LockManager
slug: Web/API/LockManager
page-type: web-api-interface
browser-compat: api.LockManager
---

{{APIRef("Web Locks API")}}{{securecontext_header}} {{AvailableInWorkers}}

رابط‌های **`LockManager`** در [Web Locks API](/en-US/docs/Web/API/Web_Locks_API) روش‌هایی برای درخواست یک شیء {{domxref('Lock')}} جدید و پرس‌وجو درباره یک شیء `Lock` موجود فراهم می‌کند. برای دریافت یک نمونه از `LockManager`، با {{domxref('navigator.locks')}} تماس بگیرید.

## روش‌های نمونه

- {{domxref('LockManager.request()')}}
  - : یک شیء {{domxref('Lock')}} را با پارامترهایی که نام و ویژگی‌های آن را مشخص می‌کند درخواست می‌کند.
- {{domxref('LockManager.query()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک شیء حاوی اطلاعاتی درباره قفل‌های نگه‌داشته‌شده و در انتظار resolve می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}