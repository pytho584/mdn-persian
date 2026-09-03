---
title: "Navigator: login property"
short-title: login
slug: Web/API/Navigator/login
page-type: web-api-instance-property
browser-compat: api.Navigator.login
---

{{securecontext_header}}{{APIRef("FedCM API")}}

خاصیت فقط‌خواندنی **`login`** در رابط {{domxref("Navigator")}} دسترسی به شیء {{domxref("NavigatorLogin")}} مرورگر را فراهم می‌کند. یک ارائه‌دهنده هویت فدرال (IdP) می‌تواند از این شیء برای تنظیم وضعیت ورود خود هنگام ورود یا خروج کاربر از IdP استفاده کند.

برای جزئیات بیشتر درباره نحوه استفاده از این ویژگی، به [به‌روزرسانی وضعیت ورود با استفاده از API وضعیت ورود](/en-US/docs/Web/API/FedCM_API/IDP_integration#update_login_status_using_the_login_status_api) مراجعه کنید.

## مقدار

یک شیء از نوع {{domxref("NavigatorLogin")}}.

## مثال‌ها

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

- [API مدیریت اعتبار فدرال (FedCM)](/en-US/docs/Web/API/FedCM_API)