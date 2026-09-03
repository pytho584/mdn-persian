```markdown
---
title: "PreferenceManager: colorScheme property"
short-title: colorScheme
slug: Web/API/PreferenceManager/colorScheme
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceManager.colorScheme
spec-urls: https://drafts.csswg.org/mediaqueries-5/#color-scheme-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`colorScheme`** در رابط {{domxref("PreferenceManager")}} یک {{domxref("PreferenceObject")}} برمی‌گرداند که برای لغو (override) ترجیح کاربر برای [طرح رنگ](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-color-scheme) سایت استفاده می‌شود.

مقادیر معتبر برای تنظیم {{domxref("PreferenceObject.value")}} در `colorScheme`، `dark` و `light` هستند.

## مقدار

یک {{domxref("PreferenceObject")}} که برای لغو ترجیح کاربر برای [طرح رنگ](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-color-scheme) سایت استفاده می‌شود.

## مثال‌ها

### استفاده پایه

این مثال نحوه پرس‌وجو از طرح رنگ ترجیحی کاربر را نشان می‌دهد.

```js
if (navigator.preferences.colorScheme.value === "dark") {
  // The user prefers a dark color scheme.
} else {
  // The user prefers a light color scheme.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```