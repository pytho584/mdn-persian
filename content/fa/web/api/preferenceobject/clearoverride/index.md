```
---
title: "PreferenceObject: clearOverride() method"
short-title: clearOverride()
slug: Web/API/PreferenceObject/clearOverride
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PreferenceObject.clearOverride
spec-urls: https://drafts.csswg.org/mediaqueries-5/#clear-override-method
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد `clearOverride` از رابط {{domxref("PreferenceObject")}} مقدار {{domxref("PreferenceObject.override", "override")}} را بازنشانی می‌کند.

## نحو

```js-nolint
clearOverrides()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### استفادهٔ پایه

مثال زیر، مقدار override مربوط به [طرح رنگی](/en-US/docs/Web/API/PreferenceObject/colorScheme) را پاک می‌کند.

```js
navigator.preferences.colorScheme.clearOverride();
console.log(navigator.preferences.colorScheme.override);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```