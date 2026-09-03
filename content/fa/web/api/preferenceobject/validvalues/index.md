---
title: "PreferenceObject: validValues property"
short-title: validValues
slug: Web/API/PreferenceObject/validValues
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PreferenceObject.validValues
spec-urls: https://drafts.csswg.org/mediaqueries-5/#valid-values-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`validValues`** از اینترفیس {{domxref("PreferenceObject")}} یک آرایه‌ی فقط‌خواندنی از مقدارهایی را برمی‌گرداند که هنگام بازنویسی (override) پذیرفته می‌شوند.

## validValues

آرایه‌ای شامل مقدارهای معتبر برای بازنویسی مقدار {{domxref("PreferenceObject")}}.

## نمونه‌ها

### استفاده‌ی پایه

این مثال نشان می‌دهد که چگونه می‌توان تمام مقدارهای کنتراست ممکن را در کنسول ثبت کرد.

```js
console.log(navigator.preferences.contrast.validValues);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}