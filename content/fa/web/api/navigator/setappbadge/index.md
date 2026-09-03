---
title: "Navigator: setAppBadge() method"
short-title: setAppBadge()
slug: Web/API/Navigator/setAppBadge
page-type: web-api-instance-method
browser-compat: api.Navigator.setAppBadge
---

{{APIRef("Badging API")}}{{securecontext_header}}

متد **`setAppBadge()`** از رابط {{domxref("Navigator")}} یک نشان (badge) روی نماد مرتبط با این برنامه تنظیم می‌کند. اگر مقداری به متد ارسال شود، آن مقدار به عنوان مقدار نشان تنظیم خواهد شد. در غیر این صورت، نشان به صورت یک نقطه یا سایر نشانگرهای تعریف‌شده توسط سکو (platform) نمایش داده می‌شود.

## Syntax

```js-nolint
setAppBadge()
setAppBadge(contents)
```

### Parameters

- `contents` {{optional_inline}}
  - : یک {{jsxref("Number")}} که به عنوان مقدار نشان استفاده می‌شود. اگر `contents` برابر `0` باشد، نشان به `nothing` تنظیم می‌شود که نشان‌دهنده پاک شدن نشان است.

### Return value

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند به طور کامل فعال نباشد پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر فراخوانی توسط [سیاست همان‌خاستگاهی](/en-US/docs/Web/Security/Defenses/Same-origin_policy) مسدود شده باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برابر `granted` نباشد پرتاب می‌شود.

## Examples

در مثال زیر، تعداد پیام‌های خوانده‌نشده به `setAppBadge()` ارسال شده است. سپس نشان باید عدد `30` را نمایش دهد.

```js
const unread = 30;
navigator.setAppBadge(unread);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Badging for app icons](https://developer.chrome.com/docs/capabilities/web-apis/badging-api/)