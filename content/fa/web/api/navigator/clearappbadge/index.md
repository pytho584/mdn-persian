---
title: "Navigator: clearAppBadge() method"
short-title: clearAppBadge()
slug: Web/API/Navigator/clearAppBadge
page-type: web-api-instance-method
browser-compat: api.Navigator.clearAppBadge
---

{{APIRef("Badging API")}}{{securecontext_header}}

متد **`clearAppBadge()`** از رابط {{domxref("Navigator")}} نشان (badge) روی آیکون برنامهٔ جاری را با تنظیم آن به `nothing` پاک می‌کند. مقدار `nothing` نشان می‌دهد که هیچ نشانی در حال حاضر تنظیم نشده است، و وضعیت نشان _پاک شده_ است.

## نحو (Syntax)

```js-nolint
clearAppBadge()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند کاملاً فعال نباشد پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر فراخوانی توسط [سیاست همان‌مبدأ](/en-US/docs/Web/Security/Defenses/Same-origin_policy) مسدود شده باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برابر با `granted` نباشد پرتاب می‌شود.

## مثال‌ها

پس از خوانده شدن تمام پیام‌ها در یک برنامه، `clearAppBadge()` را فراخوانی کنید تا نشان پاک شود و اعلان حذف شود.

```js
navigator.clearAppBadge();
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [نشان‌گذاری برای آیکون‌های برنامه](https://developer.chrome.com/docs/capabilities/web-apis/badging-api/)