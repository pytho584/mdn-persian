```
---
title: "PushManager: hasPermission() method"
short-title: hasPermission()
slug: Web/API/PushManager/hasPermission
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.PushManager.hasPermission
---

{{ApiRef("Push API")}}{{deprecated_header}}{{non-standard_header}}{{AvailableInWorkers}}

متد **`PushManager.hasPermission()`** از رابط {{domxref("PushManager")}} یک {{jsxref("Promise")}} برمی‌گرداند که به `PushPermissionStatus` برنامهٔ وب درخواست‌کننده حل می‌شود؛ این وضعیت یکی از مقادیر `granted`، `denied` یا `default` خواهد بود.

> [!NOTE]
> این قابلیت با متد {{domxref("PushManager.permissionState()")}} جایگزین شده است.

## نحو

```js-nolint
hasPermission()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به `PushPermissionStatus` حل می‌شود.

## مثال‌ها

```js
// TBD
```

## مشخصات

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست و دیگر در مسیر استاندارد شدن قرار ندارد.

## سازگاری مرورگر

{{Compat}}
```