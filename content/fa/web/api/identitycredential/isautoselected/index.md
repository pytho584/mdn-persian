---
title: "IdentityCredential: isAutoSelected property"
---

---
title: "IdentityCredential: isAutoSelected property"
short-title: isAutoSelected
slug: Web/API/IdentityCredential/isAutoSelected
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdentityCredential.isAutoSelected
---

{{securecontext_header}}{{APIRef("FedCM API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`isAutoSelected`** در رابط {{domxref("IdentityCredential")}} نشان می‌دهد که آیا جریان ورود فدرال با استفاده از [احراز هویت مجدد خودکار](/en-US/docs/Web/API/FedCM_API/RP_sign-in#auto-reauthentication) (یعنی بدون دخالت کاربر) انجام شده است یا خیر.

احراز هویت مجدد خودکار می‌تواند زمانی رخ دهد که فراخوانی {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} با مقدار `"optional"` یا `"silent"` برای گزینه [`mediation`](/en-US/docs/Web/API/CredentialsContainer/get#mediation) صادر شود. برای یک {{glossary("Relying party", "relying party")}} (RP) مفید است که بداند آیا احراز هویت مجدد خودکار رخ داده است؛ هم برای ارزیابی تحلیل‌ها و عملکرد و هم برای اهداف تجربه کاربری (UX). ورود خودکار ممکن است به جریان رابط کاربری متفاوتی نسبت به ورود غیرخودکار نیاز داشته باشد.

## مقدار

یک مقدار بولی. `true` نشان می‌دهد که احراز هویت مجدد خودکار استفاده شده است؛ `false` نشان می‌دهد که استفاده نشده است.

## مثال‌ها

### ورود فدرال پایه و دسترسی به `isAutoSelected`

طرف‌های متکی (RP) می‌توانند با فراخوانی `navigator.credentials.get()` و ارسال گزینه `identity`، درخواست ورود کاربران به RP را از طریق یک {{glossary("Identity provider", "IdP")}} و با استفاده از فدراسیون هویت انجام دهند. رفتار احراز هویت مجدد خودکار با گزینه [`mediation`](/en-US/docs/Web/API/CredentialsContainer/get#mediation) در فراخوانی `get()` کنترل می‌شود:

```js
async function signIn() {
  const identityCredential = await navigator.credentials.get({
    identity: {
      providers: [
        {
          configURL: "https://accounts.idp.example/config.json",
          clientId: "********",
        },
      ],
    },
    mediation: "optional", // this is the default
  });

  // isAutoSelected is true if auto-reauthentication occurred.
  const isAutoSelected = identityCredential.isAutoSelected;
}
```

یک فراخوانی موفق {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} که شامل گزینه `identity` باشد، با یک نمونه `IdentityCredential` تکمیل (resolve) می‌شود. می‌توان از این نمونه برای دسترسی به ویژگی `isAutoSelected` استفاده کرد: اگر احراز هویت مجدد خودکار رخ داده باشد، این ویژگی برابر `true` خواهد بود.

برای جزئیات بیشتر درباره نحوه کار این سازوکار، [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) را ببینید. این فراخوانی، جریان ورود به سامانه را که در [جریان ورود FedCM](/en-US/docs/Web/API/FedCM_API/RP_sign-in#fedcm_sign-in_flow) شرح داده شده است، آغاز می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview)