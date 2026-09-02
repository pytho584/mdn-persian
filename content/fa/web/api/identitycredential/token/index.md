---
title: "IdentityCredential: token property"
---

---
title: "IdentityCredential: token property"
short-title: token
slug: Web/API/IdentityCredential/token
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdentityCredential.token
---

{{APIRef("FedCM API")}}{{SeeCompatTable}}{{SecureContext_Header}}

خاصیت فقط‌خواندنی **`token`** در رابط {{domxref("IdentityCredential")}} توکنی را بازمی‌گرداند که برای تأیید ورود مرتبط استفاده می‌شود.

API FedCM ساختار شیء `token` یا اینکه RP (طرف متکی) باید با آن چه کند را تعریف نمی‌کند: این کاملاً به پروتکل هویت فدرال‌شده‌ای بستگی دارد که IdP (فراهم‌کننده هویت) پیاده‌سازی می‌کند.

هنگامی که یک RP (طرف متکی) تصمیم به کار با یک IdP (فراهم‌کننده هویت) خاص می‌گیرد، آن IdP دستورالعمل‌هایی را برای نحوه تفسیر و استفاده از مقدار `token` بازگشتی ارائه می‌دهد.

## مقدار

هر نوعی.

## مثال‌ها

### ورود فدرال ساده و دسترسی به `token`

طرف‌های متکی (RPها) می‌توانند متد `navigator.credentials.get()` را با گزینه `identity` فراخوانی کنند تا از کاربران بخواهند از طریق یک فراهم‌کننده هویت (IdP) با استفاده از هویت فدرال وارد سیستم شوند. یک درخواست معمولی به این شکل است:

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

  console.log(identityCredential.token);
}
```

یک فراخوانی موفق {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} که شامل گزینه `identity` باشد، با یک نمونه `IdentityCredential` تکمیل می‌شود که می‌توان از آن برای دسترسی به `token` استفاده‌شده برای تأیید ورود بهره برد.

برای جزئیات بیشتر در مورد نحوه کار این موضوع، به [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) مراجعه کنید. این فراخوانی جریان ورود شرح‌داده‌شده در [FedCM sign-in flow](/en-US/docs/Web/API/FedCM_API/RP_sign-in#fedcm_sign-in_flow) را آغاز می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview)