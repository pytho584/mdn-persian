---
title: "IdentityCredential: disconnect() static method"
---
---
title: "IdentityCredential: disconnect() static method"
short-title: disconnect()
slug: Web/API/IdentityCredential/disconnect_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.IdentityCredential.disconnect_static
---

{{APIRef("FedCM API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد استاتیک **`disconnect()`** از رابط {{domxref("IdentityCredential")}} یک حساب ورود فدرال مشخصشده را از {{glossary("Identity provider", "IdP")}} که برای دریافت اعتبارنامه استفاده شده بود، قطع میکند.

پس از این کار، استفاده از آن حساب برای ورود فدرال نیازمند شروع دوباره فرایند ورود فدرال است.

## Syntax

```js-nolint
IdentityCredential.disconnect(options)
```

### Parameters

- `options`
  - : یک شیء گزینه‌ها که می‌تواند شامل ویژگی‌های زیر باشد:
    - `accountHint`
      - : یک رشته که نشانه‌ای از حساب را مشخص می‌کند و IdP از آن برای شناسایی حسابی که باید قطع شود استفاده می‌کند. این نشانه می‌تواند هر رشته دلخواهی باشد تا زمانی که [نقطه پایانی قطع اتصال](/en-US/docs/Web/API/FedCM_API/IDP_integration#the_disconnect_endpoint) بتواند حساب را شناسایی کند — برای مثال یک آدرس ایمیل یا شناسه کاربر. این لزوماً با شناسه حسابی که توسط [نقطه پایانی لیست حساب‌ها](/en-US/docs/Web/API/FedCM_API/IDP_integration#the_accounts_list_endpoint) ارائه شده است مطابقت ندارد.
    - `clientId`
      - : یک رشته که شناسه مشتری {{glossary("Relying party", "RP")}} را مشخص می‌کند، همانطور که در ویژگی `providers` [`clientId`](/en-US/docs/Web/API/IdentityCredentialRequestOptions#clientid) در هنگام ورود تعیین شده است.
    - `configURL`
      - : یک رشته که URL فایل پیکربندی IdP را مشخص می‌کند، همانطور که در ویژگی `providers` [`configURL`](/en-US/docs/Web/API/IdentityCredentialRequestOptions#configurl) در هنگام ورود تعیین شده است.

### Return value

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} fulfilled می‌شود.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - `configURL` IdP نامعتبر است یا فاقد `disconnect_endpoint` است.
    - مبدأ سند با `configURL` مطابقت ندارد.
- `NetworkError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - مرورگر قادر به اتصال به IdP نیست.
    - درخواست توسط [`connect-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/connect-src) {{httpheader("Content-Security-Policy")}} ممنوع شده است.
    - قبلاً فراخوانی `disconnect()` دیگری انجام شده که هنوز حل نشده است.
    - API FedCM در سطح جهانی غیرفعال شده است.
    - `configURL` IdP نه امن است و نه [به طور بالقوه قابل اعتماد](/en-US/docs/Web/Security/Defenses/Secure_Contexts#potentially_trustworthy_origins).
- `NotAllowedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود: اگر `<iframe>` جاسازیشده دارای {{httpheader("Permissions-Policy/identity-credentials-get", "identity-credentials-get")}} [Permissions-Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم شده برای اجازه استفاده از `disconnect()` نباشد، یا اگر API FedCM توسط یک خط‌مشی تعیین‌شده در سند سطح بالا به صورت جهانی غیرفعال شده باشد.

## Examples

### استفاده پایه از `disconnect()`

RP می‌تواند یک حساب ورود فدرال مشخصشده را از IdP مرتبط با فراخوانی `disconnect()` قطع کند. این تابع می‌تواند از یک فریم RP سطح بالا فراخوانی شود.

```js
IdentityCredential.disconnect({
  configURL: "https://idp.example.com/config.json",
  clientId: "rp123",
  accountHint: "account456",
});
```

برای اینکه فراخوانی `disconnect()` کار کند، IdP باید یک [`disconnect_endpoint`](/en-US/docs/Web/API/FedCM_API/IDP_integration#disconnect_endpoint) در فایل پیکربندی خود داشته باشد. برای جزئیات بیشتر در مورد ارتباط HTTP زیربنایی، به [نقطه پایانی قطع اتصال](/en-US/docs/Web/API/FedCM_API/IDP_integration#the_disconnect_endpoint) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview) در developer.chrome.com (2023)