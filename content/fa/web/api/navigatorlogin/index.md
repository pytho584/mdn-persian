---
title: "NavigatorLogin"
slug: Web/API/NavigatorLogin
page-type: web-api-interface
browser-compat: api.NavigatorLogin
---

{{securecontext_header}}{{APIRef("FedCM API")}}

رابط **`NavigatorLogin`** از [API مدیریت اعتبارنامه فدرال (FedCM)](/en-US/docs/Web/API/FedCM_API) عملکرد ورود به سیستم را برای ارائه‌دهندگان هویت فدرال (IdP) تعریف می‌کند. به طور خاص، این رابط به یک ارائه‌دهنده هویت فدرال (IdP) اجازه می‌دهد تا وضعیت ورود خود را هنگامی که کاربر وارد IdP می‌شود یا از آن خارج می‌شود، تنظیم کند.

برای جزئیات بیشتر در مورد نحوه استفاده از این قابلیت، به [به‌روزرسانی وضعیت ورود با استفاده از Login Status API](/en-US/docs/Web/API/FedCM_API/IDP_integration#update_login_status_using_the_login_status_api) مراجعه کنید.

`NavigatorLogin` از طریق ویژگی {{domxref("Navigator.login")}} قابل دسترسی است.

{{InheritanceDiagram}}

## روش‌های نمونه

- {{domxref("NavigatorLogin.setStatus", "setStatus()")}}
  - وضعیت ورود یک ارائه‌دهنده هویت فدرال (IdP) را هنگامی که از مبدأ IdP فراخوانی می‌شود، تنظیم می‌کند. منظور از "وضعیت ورود" این است که "آیا کاربرانی در مرورگر فعلی وارد IdP شده‌اند یا خیر".

## نمونه‌ها

```js
/* Set logged-in status */
navigator.login.setStatus("logged-in");

/* Set logged-out status */
navigator.login.setStatus("logged-out");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Federated Credential Management (FedCM) API](/en-US/docs/Web/API/FedCM_API)