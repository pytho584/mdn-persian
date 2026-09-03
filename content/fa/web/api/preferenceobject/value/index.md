---
title: "PreferenceObject: value property"
short-title: value
slug: Web/API/PreferenceObject/value
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceObject.value
spec-urls: https://drafts.csswg.org/mediaqueries-5/#preference-value-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`value`** در رابط {{domxref("PreferenceManager")}}، مقدار جایگزین (override) یک ترجیح (preference) را در صورت تنظیم بودن برمی‌گرداند؛ در غیر این صورت، مقدار تعریف‌شده توسط عامل کاربر (UA) را بازمی‌گرداند.

## مقدار

در صورت تنظیم بودن، مقدار جایگزین رابط {{domxref("PreferenceObject")}}؛ در غیر این صورت، مقدار تعریف‌شده توسط عامل کاربر.

## مثال‌ها

### استفادهٔ پایه

این مثال نحوهٔ پرس‌وجو از ترجیح کاربر برای کاهش حرکت (reduced motion) را نشان می‌دهد.

```js
if (navigator.preferences.reducedMotion.value === "reduce") {
  // The user prefers reduced motion.
} else {
  // The user has stated no preference regarding motion.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}