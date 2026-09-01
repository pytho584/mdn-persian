---
title: "FeaturePolicy: allowsFeature() method"
short-title: allowsFeature()
slug: Web/API/FeaturePolicy/allowsFeature
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FeaturePolicy.allowsFeature
---

{{APIRef("Feature Policy API")}}{{SeeCompatTable}}{{non-standard_header}}

متد **`allowsFeature()`** از رابط {{DOMxRef("FeaturePolicy")}} امکان بررسی دستورهای جداگانه‌ی [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) اجراشده روی آن را فراهم می‌کند. این متد یک {{JSxRef("Boolean")}} برمی‌گرداند که اگر و فقط اگر ویژگی مشخص‌شده در زمینه‌ی مشخص‌شده (یا در زمینه‌ی پیش‌فرض، اگر زمینه‌ای مشخص نشده باشد) مجاز باشد، مقدار آن `true` است.

## سینتکس

```js-nolint
allowsFeature(feature)
allowsFeature(feature, origin)
```

### پارامترها

- `feature`
  - : نام ویژگی خاصی که می‌خواهید در دسترس بودن آن را بررسی کنید.
- `origin` {{Optional_inline}}
  - : نام مبدأ خاصی که می‌خواهید در دسترس بودن آن را بررسی کنید. اگر مشخص نشود، مبدأ پیش‌فرض استفاده خواهد شد.

### مقدار بازگشتی

یک {{JSxRef("Boolean")}} که اگر و فقط اگر ویژگی مجاز باشد `true` است.

## مثال

مثال زیر بررسی می‌کند که آیا سند طبق Permissions Policy اجازه‌ی استفاده از API دوربین را دارد یا خیر. توجه داشته باشید که اگر کاربر هنوز مجوز مربوطه را اعطا نکرده باشد، API دوربین ممکن است توسط Permissions API محدود شده باشد.

```js
// First, get the Feature Policy object
const featurePolicy = document.featurePolicy;

// Then query feature for specific
const allowed = featurePolicy.allowsFeature("camera");

if (allowed) {
  console.log("FP allows camera.");
} else {
  console.log("FP does not allows camera.");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}