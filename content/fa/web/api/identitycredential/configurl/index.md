```yaml
---
title: "IdentityCredential: configURL property"
short-title: configURL
slug: Web/API/IdentityCredential/configURL
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdentityCredential.configURL
---

{{APIRef("FedCM API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط خواندنی **`configURL`** در رابط {{domxref("IdentityCredential")}} یک رشته را برمی‌گرداند که URL فایل پیکربندی ارائه‌دهنده هویت (IdP) مورد استفاده برای ورود به سیستم را مشخص می‌کند.

برای اطلاعات بیشتر، [ارائه یک فایل پیکربندی و نقاط پایانی](/en-US/docs/Web/API/FedCM_API/IDP_integration#provide_a_config_file_and_endpoints) را ببینید.

## مقدار

یک رشته.

## مثال‌ها

### ورود فدرال پایه و دسترسی به `configURL`

طرف‌های متکی (RP) می‌توانند با گزینه `identity` متد `navigator.credentials.get()` را فراخوانی کنند تا درخواستی برای ورود کاربران به RP از طریق یک ارائه‌دهنده هویت (IdP) با استفاده از فدراسیون هویت ارسال کنند. یک درخواست که یک ارائه‌دهنده را مشخص می‌کند به این شکل است:

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

  console.log(identityCredential.configURL);
}
```

یک فراخوانی موفق {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} که شامل گزینه `identity` است، با یک نمونه `IdentityCredential` تکمیل می‌شود که می‌توان از آن برای دسترسی به `configURL` ارائه‌دهنده هویت مورد استفاده برای ورود استفاده کرد.

برای جزئیات بیشتر در مورد نحوه کار این API، [API مدیریت اعتبارنامه فدرال (FedCM)](/en-US/docs/Web/API/FedCM_API) را بررسی کنید. این فراخوانی جریان ورود به سیستم را که در [جریان ورود FedCM](/en-US/docs/Web/API/FedCM_API/RP_sign-in#fedcm_sign-in_flow) توضیح داده شده است، آغاز می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [API مدیریت اعتبارنامه فدرال](https://developer.chrome.com/docs/identity/fedcm/overview)