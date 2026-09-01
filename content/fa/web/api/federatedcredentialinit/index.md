---
title: "FederatedCredentialInit"
---

---
title: FederatedCredentialInit
slug: Web/API/FederatedCredentialInit
page-type: web-api-interface
spec-urls: https://w3c.github.io/webappsec-credential-management/#dom-federatedcredential-federatedcredential
---

{{APIRef("Credential Management API")}}

دیکشنری **`FederatedCredentialInit`** شیءای را که به‌عنوان مقدار گزینهٔ `federated` به {{domxref("CredentialsContainer.create()")}} ارسال می‌شود، نشان می‌دهد؛ یعنی هنگام ایجاد یک شیء {{domxref("FederatedCredential")}} که نمایانگر اعتبارنامه‌ای مرتبط با یک تأمین‌کنندهٔ هویت فدرال است.

> [!NOTE]
> [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) جایگزین رابط {{domxref("FederatedCredential")}} شده و به‌جای آن از رابط {{domxref("IdentityCredential")}} استفاده می‌کند.
>
> دیکشنری `FederatedCredentialInit` هنگام کار با رابط `IdentityCredential` استفاده نمی‌شود.

## ویژگی‌های نمونه

- `iconURL` {{optional_inline}}
  - : یک رشته که نشانی (URL) آیکون یا آواتار مرتبط با اعتبارنامه را نشان می‌دهد.
- `id`
  - : یک رشته که شناسهٔ یکتای اعتبارنامه را نشان می‌دهد.
- `name` {{optional_inline}}
  - : یک رشته که نام کاربری اعتبارنامه را نشان می‌دهد.
- `origin`
  - : یک رشته که مبدأ (origin) اعتبارنامه را نشان می‌دهد. اشیاء {{domxref("FederatedCredential")}} به مبدأ وابسته هستند (origin-bound)؛ به این معنی که فقط در همان مبدأ مشخصی که برای آن در نظر گرفته شده‌اند قابل استفاده خواهند بود.
- `protocol` {{optional_inline}}
  - : یک رشته که پروتکل تأمین‌کنندهٔ هویت فدرال اعتبارنامه را نشان می‌دهد (مثلاً `"openidconnect"`).
- `provider`
  - : یک رشته که تأمین‌کنندهٔ هویت فدرال اعتبارنامه را نشان می‌دهد (مثلاً `"https://www.facebook.com"` یا `"https://accounts.google.com"`).

## مثال‌ها

### ایجاد یک اعتبارنامهٔ هویت فدرال

```js
const credInit = {
  id: "1234",
  name: "Serpentina",
  origin: "https://example.org",
  protocol: "openidconnect",
  provider: "https://provider.example.org",
};

const makeCredential = document.querySelector("#make-credential");

makeCredential.addEventListener("click", async () => {
  const cred = await navigator.credentials.create({
    federated: credInit,
  });
  console.log(cred.name);
  console.log(cred.provider);
});
```

## مشخصات

{{Specifications}}