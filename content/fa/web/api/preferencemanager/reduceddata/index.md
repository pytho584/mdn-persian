---
title: "PreferenceManager: reducedData property"
short-title: reducedData
slug: Web/API/PreferenceManager/reducedData
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceManager.reducedData
spec-urls: https://drafts.csswg.org/mediaqueries-5/#reduced-data-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط-خواندنی **`reducedData`** از رابط {{domxref("PreferenceManager")}} یک {{domxref("PreferenceObject")}} برمی‌گرداند که برای لغو اولویت کاربر در مورد [کاهش داده](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-data) سایت استفاده می‌شود.

مقادیر معتبر `reducedData` برای {{domxref("PreferenceObject.value")}} عبارتند از `reduce` و `no-preference`.

## مقدار

یک {{domxref("PreferenceObject")}} که برای لغو اولویت کاربر در مورد [کاهش داده](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-data) سایت استفاده می‌شود.

## مثال‌ها

### استفاده پایه

این مثال نحوه پرس‌وجو از اولویت کاهش داده کاربر را نشان می‌دهد.

```js
if (navigator.preferences.reducedData.value === "reduce") {
  // The user prefers you use less data.
} else {
  // The user has stated no preference regarding data use.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}