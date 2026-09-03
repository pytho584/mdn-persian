---
title: PreferenceManager
slug: Web/API/PreferenceManager
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PreferenceManager
spec-urls: https://drafts.csswg.org/mediaqueries-5/#preference-manager
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط **`PreferenceManager`** از [User Preferences API](/en-US/docs/Web/API/User_Preferences_API) دسترسی به اشیاء {{domxref("PreferenceObject")}} را فراهم می‌کند که برای جست‌وجو و تغییر ترجیحات کاربر استفاده می‌شوند.

`PreferenceManager` سند جاری از طریق ویژگی {{domxref("Navigator.preferences")}} قابل دسترسی است.

رابط `PreferenceManager` از {{domxref("EventTarget")}} ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PreferenceManager.colorScheme")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("PreferenceObject")}} که برای بازنویسی ترجیح کاربر برای [طرح رنگ](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-color-scheme) سایت استفاده می‌شود.
- {{domxref("PreferenceManager.contrast")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("PreferenceObject")}} که برای بازنویسی ترجیح کاربر برای [کنتراست](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-contrast) سایت استفاده می‌شود.
- {{domxref("PreferenceManager.reducedMotion")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("PreferenceObject")}} که برای بازنویسی ترجیح کاربر برای [حرکت کاهش‌یافته](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) سایت استفاده می‌شود.
- {{domxref("PreferenceManager.reducedTransparency")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("PreferenceObject")}} که برای بازنویسی ترجیح کاربر برای [شفافیت کاهش‌یافته](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-transparency) سایت استفاده می‌شود.
- {{domxref("PreferenceManager.reducedData")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("PreferenceObject")}} که برای بازنویسی ترجیح کاربر برای [داده کاهش‌یافته](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-data) سایت استفاده می‌شود.

## مثال‌ها

### استفاده پایه

این مثال نشان می‌دهد که چگونه می‌توان طرح رنگ ترجیحی کاربر را پرس‌وجو کرد.

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