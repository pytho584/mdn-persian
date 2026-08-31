---
title: "BackgroundFetchRegistration: abort() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/abort"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: abort() method"
short-title: abort()
slug: Web/API/BackgroundFetchRegistration/abort
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.abort
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

**`abort()`** method از رابط {{domxref("BackgroundFetchRegistration")}} یک دریافت (fetch) فعال در پس‌زمینه را لغو می‌کند.

## Syntax

```js-nolint
abort()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با `true` حل می‌شود اگر دریافت با موفقیت لغو شود.

## مثال‌ها

از `abort()` برای پایان دادن به یک دریافت در حال انجام در پس‌زمینه استفاده کنید.

```js
bgFetch.abort();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}