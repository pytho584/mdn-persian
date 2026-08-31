---
title: Credential
slug: Web/API/Credential
page-type: web-api-interface
browser-compat: api.Credential
---

{{APIRef("Credential Management API")}}{{securecontext_header}}

رابط **`Credential`** از [API مدیریت اعتبارنامه](/en-US/docs/Web/API/Credential_Management_API) اطلاعاتی درباره یک موجودیت (معمولاً یک کاربر) فراهم می‌کند که معمولاً به عنوان پیش‌نیاز یک تصمیم‌گیری اعتماد استفاده می‌شود.

اشیاء `Credential` می‌توانند از انواع زیر باشند:

- {{domxref("FederatedCredential")}}
- {{domxref("IdentityCredential")}}
- {{domxref("PasswordCredential")}}
- {{domxref("PublicKeyCredential")}}
- {{domxref("OTPCredential")}}

## خصوصیات نمونه

- {{domxref("Credential.id")}} {{ReadOnlyInline}}
  - : یک رشته شامل شناسه اعتبارنامه برمی‌گرداند. این می‌تواند یکی از GUID، نام کاربری یا آدرس ایمیل باشد.
- {{domxref("Credential.type")}} {{ReadOnlyInline}}
  - : یک رشته شامل نوع اعتبارنامه برمی‌گرداند. مقادیر معتبر عبارتند از `password`، `federated`، `public-key`، `identity` و `otp`. (برای {{domxref("PasswordCredential")}}، {{domxref("FederatedCredential")}}، {{domxref("PublicKeyCredential")}}، {{domxref("IdentityCredential")}} و {{domxref("OTPCredential")}})

## روش‌های ایستا

- {{domxref("Credential.isConditionalMediationAvailable_static", "Credential.isConditionalMediationAvailable()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که همیشه با مقدار `false` حل می‌شود. زیرکلاس‌ها می‌توانند این مقدار را بازنویسی کنند.

## مثال‌ها

```js
const pwdCredential = new PasswordCredential({
  id: "example-username", // Username/ID
  name: "Carina Anand", // Display name
  password: "correct horse battery staple", // Password
});

console.assert(pwdCredential.type === "password");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}