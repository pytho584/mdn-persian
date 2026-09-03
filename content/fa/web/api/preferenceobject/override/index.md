---
title: "PreferenceObject: override property"
---

---
title: "PreferenceObject: override property"
short-title: override
slug: Web/API/PreferenceObject/override
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PreferenceObject.override
spec-urls: https://drafts.csswg.org/mediaqueries-5/#override-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط‌خواندنیِ **`override`** در رابط {{domxref("PreferenceObject")}}، اگر برای یک ترجیح (preference) مقدار جایگزین (override) تنظیم شده باشد، آن را برمی‌گرداند؛ در غیر این صورت، `null` را برمی‌گرداند.

## مقدار

مقدار override رابط {{domxref("PreferenceObject")}}، در صورتی که تنظیم شده باشد؛ در غیر این صورت، اگر هیچ override تنظیم نشده باشد، `null` خواهد بود.

## مثال‌ها

## استفادهٔ پایه

این مثال نشان می‌دهد که چگونه می‌توان بین ترجیحِ «طرح‌رنگ» (color scheme) تنظیم‌شده توسط عامل کاربر (user agent) و یک override برنامه‌ای تمایز قائل شد.

```js
if (navigator.preferences.colorScheme.override === null) {
  console.log(
    "The user agent set the following color scheme:",
    navigator.preferences.colorScheme.value,
  );
} else {
  console.log(
    "The following color scheme was set programmatically:",
    navigator.preferences.colorScheme.override,
  );
}
```

## مشخصات فنی

{{Specifications}}

## سازگاری مرورگر

{{Compat}}