---
title: "PreferenceObject: requestOverride() method"
short-title: requestOverride()
slug: Web/API/PreferenceObject/requestOverride
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PreferenceObject.requestOverride
spec-urls: https://drafts.csswg.org/mediaqueries-5/#request-override-method
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`requestOverride`** در واسط {{domxref("PreferenceObject")}}، مقدار {{domxref("PreferenceObject.override", "override")}} را برای یک ترجیح مشخص تنظیم می‌کند.

## سینتکس

```js-nolint
requestOverrides(value)
```

### پارامترها

- `value`
  - : مقداری که با آن درخواستِ override انجام می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که در صورت موفقیت به {{jsxref("undefined")}} resolve می‌شود و در صورت شکست reject می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی که مقدار داده‌شده مجاز نباشد پرتاب می‌شود.

## مثال‌ها

### استفادهٔ پایه

در مثال زیر یک override برای {{domxref("PreferenceObject.colorScheme", "colorScheme")}} درخواست می‌شود:

```js
await navigator.preferences.colorScheme.requestOverride("dark");
console.log(navigator.preferences.colorScheme.override);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}