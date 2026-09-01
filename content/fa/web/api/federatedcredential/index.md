---
title: FederatedCredential
slug: Web/API/FederatedCredential
page-type: web-api-interface
status:
  - experimental
browser-compat: api.FederatedCredential
---

{{SeeCompatTable}}{{APIRef("Credential Management API")}}{{SecureContext_Header}}

رابط **`FederatedCredential`** در [Credential Management API](/en-US/docs/Web/API/Credential_Management_API) اطلاعات مربوط به اعتبارنامه‌های یک ارائه‌دهنده هویت فدرال را فراهم می‌کند. ارائه‌دهنده هویت فدرال، موجودیتی است که یک وب‌سایت به آن اعتماد می‌کند تا کاربر را به‌درستی احراز هویت کند و APIای برای این منظور در اختیار قرار می‌دهد. [OpenID Connect](https://openid.net/developers/specs/) نمونه‌ای از چارچوب‌های ارائه‌دهنده هویت فدرال است.

> [!NOTE]
> [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) راه‌حل کامل‌تری برای مدیریت فدرال‌سازی هویت در مرورگر فراهم می‌کند و از نوع {{domxref("IdentityCredential")}} استفاده می‌کند.

در مرورگرهایی که از آن پشتیبانی می‌کنند، می‌توان نمونه‌ای از این رابط را در عضو `credential` آبجکت `init` برای {{domxref("Window/fetch", "fetch()")}} سراسری قرار داد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("FederatedCredential.FederatedCredential()","FederatedCredential()")}} {{Experimental_Inline}}
  - : یک شیء `FederatedCredential` جدید می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌های نمونه از کلاس والد آن، یعنی {{domxref("Credential")}} به ارث می‌رسند._

- {{domxref("FederatedCredential.provider")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که شامل ارائه‌دهنده هویت فدرال یک اعتبارنامه است.
- {{domxref("FederatedCredential.protocol")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که شامل پروتکل هویت فدرال یک اعتبارنامه است.

## روش‌های نمونه

هیچ.

## مثال‌ها

```js
const cred = new FederatedCredential({
  id,
  name,
  provider: "https://account.google.com",
  iconURL,
});

// Store it
navigator.credentials.store(cred).then(() => {
  // Do something else.
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}