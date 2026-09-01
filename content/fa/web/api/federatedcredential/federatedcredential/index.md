---
title: "FederatedCredential: FederatedCredential() constructor"
short-title: FederatedCredential()
slug: Web/API/FederatedCredential/FederatedCredential
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.FederatedCredential.FederatedCredential
---

{{APIRef("Credential Management API")}}{{SeeCompatTable}}{{SecureContext_Header}}

سازندهٔ **`FederatedCredential()`** یک شیء {{domxref("FederatedCredential")}} جدید ایجاد می‌کند. در مرورگرهای پشتیبانی‌کننده، نمونه‌ای از این کلاس می‌تواند به‌عنوان «credential» دریافت‌شده از شیء `init` برای تابع سراسری {{domxref("Window/fetch", "fetch()")}} ارسال شود.

## نحو (Syntax)

```js-nolint
new FederatedCredential(data)
```

### پارامترها

- `data`
  - : یک شیء {{domxref("FederatedCredentialInit")}} است. شیئی با ویژگی‌های زیر:
    - `name` {{optional_inline}}
      - : رشته‌ای که نام کاربری credential را نشان می‌دهد.
    - `iconURL` {{optional_inline}}
      - : رشته‌ای که URL یک آیکون یا تصویر کاربری را نشان می‌دهد که باید با credential مرتبط شود.
    - `origin`
      - : رشته‌ای که مبدأ (origin) credential را نشان می‌دهد. اشیاء {{domxref("FederatedCredential")}} به مبدأ وابسته هستند، بنابراین فقط در همان مبدأ مشخص‌شده قابل استفاده خواهند بود.
    - `provider`
      - : رشته‌ای که ارائه‌دهندهٔ هویت فدرال credential را مشخص می‌کند؛ به‌صورت مبدأیی که ارائه‌دهنده برای ورود کاربران استفاده می‌کند (مثلاً `"https://www.facebook.com"` یا `"https://accounts.google.com"`).
    - `protocol` {{optional_inline}}
      - : رشته‌ای که پروتکل ارائه‌دهندهٔ هویت فدرال credential را نشان می‌دهد (مثلاً `"openidconnect"`).

## نمونه‌ها

### ایجاد یک credential هویت فدرال

```js
const credData = {
  id: "1234",
  name: "Serpentina",
  origin: "https://example.org",
  protocol: "openidconnect",
  provider: "https://provider.example.org",
};

const fedCred = new FederatedCredential(credData);

// ذخیرهٔ آن
navigator.credentials.store(fedCred).then(() => {
  // کار دیگری انجام بده
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}