---
title: IdentityCredential
slug: Web/API/IdentityCredential
page-type: web-api-interface
status:
  - experimental
browser-compat: api.IdentityCredential
---

{{APIRef("FedCM API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط **`IdentityCredential`** از [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) یک اعتبارنامه هویت کاربر را نشان می‌دهد که از یک ورود به سیستم فدرال موفق حاصل می‌شود.

یک فراخوانی موفق {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} که شامل یک گزینه `identity` باشد، با یک نمونه `IdentityCredential` تکمیل می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

ویژگی‌هایی را از ancestor خود، {{domxref("Credential")}} به ارث می‌برد.

- {{domxref("IdentityCredential.configURL")}} {{ReadOnlyInline}} {{experimental_inline}}
  - یک رشته که URL [فایل پیکربندی](/en-US/docs/Web/API/FedCM_API/IDP_integration#provide_a_config_file_and_endpoints) {{glossary("Identity provider", "IdP")}} مورد استفاده برای ورود را مشخص می‌کند.
- {{domxref("IdentityCredential.isAutoSelected")}} {{ReadOnlyInline}} {{experimental_inline}}
  - یک مقدار بولی که نشان می‌دهد آیا ورود فدرال با استفاده از [احراز هویت مجدد خودکار](/en-US/docs/Web/API/FedCM_API/RP_sign-in#auto-reauthentication) (یعنی بدون میانجیگری کاربر) انجام شده است یا خیر.
- {{domxref("IdentityCredential.token")}} {{experimental_inline}}
  - توکن مورد استفاده برای اعتبارسنجی ورود مرتبط را بازمی‌گرداند.

## روش‌های ایستا

- {{domxref("IdentityCredential.disconnect_static", "IdentityCredential.disconnect()")}} {{experimental_inline}}
  - حساب ورود فدرال که برای به دست آوردن اعتبارنامه استفاده شده است را قطع می‌کند.

## مثال‌ها

### ورود فدرال پایه

{{glossary("Relying party", "Relying parties")}} (RPها) می‌توانند با `navigator.credentials.get()` با گزینه `identity` تماس بگیرند تا درخواستی برای ورود کاربران به RP از طریق یک ارائه‌دهنده هویت (IdP) با استفاده از فدراسیون هویت انجام دهند. یک درخواست معمولی به این شکل است:

```js
async function signIn() {
  const identityCredential = await navigator.credentials.get({
    identity: {
      providers: [
        {
          configURL: "https://accounts.idp.example/config.json",
          clientId: "********",
          params: {/* IdP-specific parameters */},
        },
      ],
    },
  });
}
```

در صورت موفقیت، این فراخوانی با یک نمونه `IdentityCredential` تکمیل می‌شود. از این نمونه، می‌توانید مقدار {{domxref("IdentityCredential.token")}} را بازگردانید، به عنوان مثال:

```js
console.log(identityCredential.token);
```

برای جزئیات بیشتر در مورد نحوه عملکرد این، به [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) مراجعه کنید. این فراخوانی جریان ورود به سیستم توصیف شده در [FedCM sign-in flow](/en-US/docs/Web/API/FedCM_API/RP_sign-in#fedcm_sign-in_flow) را آغاز می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview)