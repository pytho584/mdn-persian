---
title: "FeaturePolicy: features() method"
short-title: features()
slug: Web/API/FeaturePolicy/features
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FeaturePolicy.features
---

{{APIRef("Feature Policy API")}}{{SeeCompatTable}}{{non-standard_header}}

متد **`features()`** در رابط {{DOMxRef("FeaturePolicy")}} فهرستی از نام تمام ویژگی‌های پشتیبانی‌شده توسط عامل کاربر (User Agent) را برمی‌گرداند. ویژگی‌ای که نامش در این فهرست دیده می‌شود ممکن است توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) بافتار اجرای فعلی مجاز نباشد و/یا به دلیل مجوزهای کاربر در دسترس نباشد.

### Syntax

```js-nolint
features()
```

### Parameters

هیچ‌کدام.

### Return value

فهرستی از رشته‌ها که نام تمام دایرکتیوهای Permissions Policy پشتیبانی‌شده توسط عامل کاربر را نشان می‌دهند.

## Example

مثال زیر تمام دستورالعمل‌های پشتیبانی‌شده را در کنسول ثبت می‌کند.

```js
// Get the FeaturePolicy object
const featurePolicy = document.featurePolicy;

// Retrieve the list of all supported Permissions Policy directives
const supportedDirectives = featurePolicy.features();

// Print out each directive into the console
for (const directive of supportedDirectives) {
  console.log(directive);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}