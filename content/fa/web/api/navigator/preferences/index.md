---
title: "Navigator: preferences property"
---

---
title: "Navigator: preferences property"
short-title: preferences
slug: Web/API/Navigator/preferences
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.preferences
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`preferences`** از رابط {{domxref("Navigator")}} یک شیء {{domxref("PreferenceManager")}} برای سند جاری بازمی‌گرداند. این نقطه ورود برای قابلیت‌های [User Preferences API](/en-US/docs/Web/API/User_Preferences_API) است.

## مقدار

یک شیء {{domxref('PreferenceManager')}}.

## مثال‌ها

### دریافت ترجیح رنگ‌بندی

این مثال نحوه پرس‌وجوی ترجیح رنگ‌بندی کاربر را نشان می‌دهد.

```js
if (navigator.preferences.colorScheme.value === "dark") {
  // کاربر رنگ‌بندی تیره را ترجیح می‌دهد.
} else {
  // کاربر رنگ‌بندی روشن را ترجیح می‌دهد.
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [User Preferences API](/en-US/docs/Web/API/User_Preferences_API)