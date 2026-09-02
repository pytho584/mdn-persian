---
title: "IdentityProvider: close() static method"
short-title: close()
slug: Web/API/IdentityProvider/close_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.IdentityProvider.close_static
---

{{securecontext_header}}{{APIRef("FedCM API")}}{{SeeCompatTable}}

متد ایستای **`close()`** از واسط {{domxref("IdentityProvider")}} یک سیگنال دستی به مرورگر می‌دهد که جریان ورود به سیستم {{glossary("Identity provider", "IdP")}} به پایان رسیده است.

`close()` باید از همان مبدأ (origin) دیالوگ ورود IdP مشخص‌شده فراخوانی شود، همان‌طور که در [پیکربندی IdP](/en-US/docs/Web/API/FedCM_API/IDP_integration#provide_a_config_file_and_endpoints) تعریف شده است.

از `close()` برای بستن دیالوگ ورود IdP زمانی استفاده می‌شود که ورود کاملاً به پایان رسیده و IdP جمع‌آوری داده‌ها از کاربر را تمام کرده است. یک مورد استفاده اصلی برای `close()` بستن دیالوگ ورود IdP در مواردی است که [وضعیت ورود مرورگر و IdP از هماهنگی خارج می‌شود](/en-US/docs/Web/API/FedCM_API/IDP_integration#what_if_the_browser_and_the_idp_login_status_become_out_of_sync) و مرورگر یک جریان ورود پویا (dynamic sign-in) را برای رفع مشکل آغاز می‌کند.

## نحو (Syntax)

```js-nolint
IdentityProvider.close()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

`undefined`.

## مثال‌ها

### استفادهٔ پایه از `IdentityProvider.close()`

```js
IdentityProvider.close();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview) در developer.chrome.com (2023)