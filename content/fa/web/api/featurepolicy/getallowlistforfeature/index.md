---
title: "FeaturePolicy: getAllowlistForFeature() method"
short-title: getAllowlistForFeature()
slug: Web/API/FeaturePolicy/getAllowlistForFeature
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FeaturePolicy.getAllowlistForFeature
---

{{APIRef("Feature Policy API")}}{{SeeCompatTable}}{{non-standard_header}}

متد **`getAllowlistForFeature()`** از رابط {{DOMxRef("FeaturePolicy")}} امکان پرس‌وجو از فهرست مجاز (allowlist) برای یک ویژگی خاص در سیاست مجوزهای (Permissions Policy) فعلی را فراهم می‌کند.

## نحو (Syntax)

```js-nolint
getAllowlistForFeature(feature)
```

### پارامترها

- `feature`
  - : نام ویژگی خاصی که می‌خواهید فهرست مجاز آن را دریافت کنید.

### مقدار بازگشتی

آرایه‌ای از رشته‌ها شامل فهرست سریالی‌شده از مبدأهای مجاز برای آن ویژگی. اگر از کاراکتر wildcard (`*`) استفاده شده باشد، آرایه شامل `*` خواهد بود.

### استثناها

اگر نام دستورالعمل Permissions Policy مشخص‌شده شناخته‌شده نباشد، تابع یک هشدار صادر می‌کند. با این حال، در این حالت نیز یک آرایه خالی برمی‌گرداند که نشان می‌دهد هیچ مبدأی اجازه استفاده از آن ویژگی را ندارد.

## مثال

مثال زیر تمام مبدأهایی را چاپ می‌کند که طبق Permissions Policy مجاز به استفاده از Camera API هستند. توجه داشته باشید که Camera API ممکن است توسط [Permissions API](/en-US/docs/Web/API/Permissions_API) نیز محدود شده باشد، اگر کاربر مجوز مربوطه را اعطا نکرده باشد.

```js
// ابتدا، شیء FeaturePolicy را دریافت کنید
const featurePolicy = document.featurePolicy;

// پرس‌وجو برای ویژگی خاص
const allowlist = featurePolicy.getAllowlistForFeature("camera");

for (const origin of allowlist) {
  console.log(origin);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}