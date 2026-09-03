---
title: "PreferenceManager: reducedTransparency property"
short-title: reducedTransparency
slug: Web/API/PreferenceManager/reducedTransparency
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceManager.reducedTransparency
spec-urls: https://drafts.csswg.org/mediaqueries-5/#reduced-transparency-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی `reducedTransparency` از رابط {{domxref("PreferenceManager")}}، شیء {{domxref("PreferenceObject")}} را بازمی‌گرداند که برای بازنویسی ترجیح کاربر دربارهٔ [کاهش شفافیت](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-transparency) سایت استفاده می‌شود.

مقادیر معتبر برای {{domxref("PreferenceObject.value")}} در `reducedTransparency` عبارت‌اند از `reduce` و `no-preference`.

## مقدار

یک {{domxref("PreferenceObject")}} که برای بازنویسی ترجیح کاربر دربارهٔ [کاهش شفافیت](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-transparency) سایت استفاده می‌شود.

## نمونه‌ها

### استفادهٔ پایه

این مثال نشان می‌دهد که چگونه می‌توان ترجیح کاربر در مورد کاهش شفافیت را بررسی کرد.

```js
if (navigator.preferences.reducedTransparency.value === "reduce") {
  // The user prefers reduced transparency.
} else {
  // The user has stated no preference regarding transparency.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}