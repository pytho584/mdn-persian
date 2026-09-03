---
title: "PreferenceManager: reducedMotion property"
short-title: reducedMotion
slug: Web/API/PreferenceManager/reducedMotion
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceManager.reducedMotion
spec-urls: https://drafts.csswg.org/mediaqueries-5/#reduced-motion-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

خاصیت فقط‌خواندنی **`reducedMotion`** در رابط {{domxref("PreferenceManager")}}، شیء {{domxref("PreferenceObject")}} را برمی‌گرداند که برای لغو ترجیح کاربر نسبت به [حرکت کم‌شده](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) سایت استفاده می‌شود.

مقادیر معتبر برای {{domxref("PreferenceObject.value")}} در `reducedMotion` عبارت‌اند از `reduce` و `no-preference`.

## مقدار

یک {{domxref("PreferenceObject")}} که برای لغو ترجیح کاربر نسبت به [حرکت کم‌شده](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) سایت استفاده می‌شود.

## مثال‌ها

### استفاده اولیه

این مثال نحوه پرس‌وجو از ترجیح کاربر برای حرکت کم‌شده را نشان می‌دهد.

```js
if (navigator.preferences.reducedMotion.value === "reduce") {
  // کاربر حرکت کم‌شده را ترجیح می‌دهد.
} else {
  // کاربر ترجیحی در مورد حرکت اعلام نکرده است.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}