---
title: "PreferenceManager: contrast property"
short-title: contrast
slug: Web/API/PreferenceManager/contrast
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceManager.contrast
spec-urls: https://drafts.csswg.org/mediaqueries-5/#contrast-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط خواندنی **`contrast`** از رابط {{domxref("PreferenceManager")}} یک {{domxref("PreferenceObject")}} را برمی‌گرداند که برای نادیده گرفتن ترجیح کاربر برای [کنتراست](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-contrast) سایت استفاده می‌شود.

مقادیر معتبر برای تنظیم `contrast` {{domxref("PreferenceObject.value")}} عبارتند از `more`، `less` و `no-preference`.

## مقدار

یک {{domxref("PreferenceObject")}} که برای نادیده گرفتن ترجیح کاربر برای [کنتراست](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-contrast) سایت استفاده می‌شود.

## مثال‌ها

### استفاده پایه

این مثال نحوه پرس‌وجو از ترجیح کنتراست کاربر را نشان می‌دهد.

```js
if (navigator.preferences.contrast.value === "more") {
  // کاربر کنتراست رنگی بالا را ترجیح می‌دهد.
} else if (navigator.preferences.contrast.value === "less") {
  // کاربر کنتراست رنگی پایین را ترجیح می‌دهد.
} else {
  // کاربر هیچ ترجیحی در مورد کنتراست رنگی اعلام نکرده است.
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}