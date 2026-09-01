---
title: FeaturePolicy
slug: Web/API/FeaturePolicy
page-type: web-api-interface
status:
  - experimental
  - non-standard
browser-compat: api.FeaturePolicy
---

{{APIRef("Feature Policy")}}{{SeeCompatTable}}{{non-standard_header}}

رابط `FeaturePolicy` نشان‌دهنده مجموعه‌ای از [سیاست‌های مجوز (Permissions Policies)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) است که در بستر اجرای فعلی اعمال می‌شوند.

## روش‌های نمونه

- {{DOMxRef("FeaturePolicy.allowsFeature")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : یک مقدار Boolean برمی‌گرداند که نشان می‌دهد آیا یک ویژگی خاص در بستر مشخص‌شده فعال است یا خیر.
- {{DOMxRef("FeaturePolicy.features")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : فهرستی از نام‌های تمام ویژگی‌های پشتیبانی‌شده توسط عامل کاربر (User Agent) برمی‌گرداند. ویژگی‌هایی که نام آنها در این فهرست ظاهر می‌شود ممکن است توسط سیاست مجوز (Permissions Policy) بستر اجرای فعلی مجاز نباشند و/یا توسط مجوزهای اعطاشده توسط کاربر محدود شده باشند.
- {{DOMxRef("FeaturePolicy.allowedFeatures")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : فهرستی از نام‌های تمام ویژگی‌های پشتیبانی‌شده توسط عامل کاربر (User Agent) و مجاز توسط سیاست مجوز (Permissions Policy) برمی‌گرداند. توجه داشته باشید که ویژگی‌های ظاهر شده در این فهرست ممکن است همچنان نیازمند مجوز کاربر باشند.
- {{DOMxRef("FeaturePolicy.getAllowlistForFeature")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : مجوز مجاز (allow) برای ویژگی مشخص‌شده را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Permissions-Policy")}}
- [حریم خصوصی، مجوزها و امنیت اطلاعات](/en-US/docs/Web/Privacy)