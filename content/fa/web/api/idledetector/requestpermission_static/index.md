---
title: "IdleDetector: requestPermission() static method"
short-title: requestPermission()
slug: Web/API/IdleDetector/requestPermission_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.IdleDetector.requestPermission_static
---

{{securecontext_header}}{{APIRef("Idle Detection API")}}{{SeeCompatTable}}

متد ایستای **`requestPermission()`** از رابط {{domxref("IdleDetector")}} یک {{jsxref('Promise')}} برمی‌گرداند که وقتی کاربر انتخاب کرد که آیا به مبدأ (origin) دسترسی به وضعیت بیکاری (idle) خود را بدهد یا نه، با یک رشته (string) حل می‌شود. در صورت پذیرش با `"granted"` و در صورت رد با `"denied"` حل می‌شود.

## نحو

```js-nolint
IdleDetector.requestPermission()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک `Promise` که با `"granted"` یا `"denied"` حل می‌شود.

## امنیت

[فعال‌سازی کاربر گذرا](/en-US/docs/Web/Security/Defenses/User_activation) (Transient user activation) مورد نیاز است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند.

## مثال‌ها

مثال زیر از یک رویداد `click` روی دکمه برای درخواست مجوز از کاربر جهت تشخیص زمانی که کاربر بیکار است استفاده می‌کند.

```js
startButton.addEventListener("click", async () => {
  if ((await IdleDetector.requestPermission()) !== "granted") {
    console.error("Idle detection permission denied.");
    return;
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}