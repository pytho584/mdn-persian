---
title: "NavigatorLogin: setStatus() method"
---

---
title: "NavigatorLogin: setStatus() method"
short-title: setStatus()
slug: Web/API/NavigatorLogin/setStatus
page-type: web-api-instance-method
browser-compat: api.NavigatorLogin.setStatus
---

{{securecontext_header}}{{APIRef("FedCM API")}}

متد **`setStatus()`** در رابط {{domxref("NavigatorLogin")}} وضعیت ورود را برای یک ارائه‌دهنده هویت فدرال (IdP) تنظیم می‌کند، زمانی که از مبدأ (origin) همان IdP فراخوانده شود. منظور ما از این کار این است که «آیا کاربرانی در مرورگر فعلی به IdP وارد شده‌اند یا نه». سایت IdP باید این متد را پس از ورود یا خروج کاربر فراخوانی کند.

مرورگر این وضعیت را برای هر IdP ذخیره می‌کند؛ سپس [FedCM API](/en-US/docs/Web/API/FedCM_API) از آن برای کاهش تعداد درخواست‌هایی که به IdP ارسال می‌کند استفاده می‌کند (چون وقتی هیچ کاربری به IdP وارد نشده باشد، نیازی نیست وقت خود را صرف درخواست حساب‌ها کند). همچنین این کار [potential timing attacks](https://github.com/w3c-fedid/FedCM/issues/447) را کاهش می‌دهد.

برای اطلاعات بیشتر درباره وضعیت ورود به FedCM، به [Update login status using the Login Status API](/en-US/docs/Web/API/FedCM_API/IDP_integration#update_login_status_using_the_login_status_api) مراجعه کنید.

## Syntax

```js-nolint
setStatus(status)
```

### Parameters

- `status`
  - : یک رشته است که وضعیت ورود را برای IdP مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"logged-in"`: حداقل یک حساب کاربری در IdP وارد شده است.
    - `"logged-out"`: هم‌اکنون همه حساب‌های کاربری IdP از سیستم خارج شده‌اند.

### Return value

یک {{jsxref("Promise")}} که با مقدار `undefined` برآورده (resolve) می‌شود.

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که دامنه فراخواننده در فریمی نباشد که تمام سطوح سلسله‌مراتب تودرتو (nesting) آن هم‌مبدأ (same-origin) هستند. چه از فریم اصلی فراخوانده شود، چه از {{htmlelement("iframe")}} که داخل فریم اصلی قرار دارد، و چه از `<iframe>` دیگری که یک یا چند سطح در داخل `<iframe>` اول تودرتو شده باشد، _همه_ سطوح سلسله‌مراتب تودرتو باید هم‌مبدأ باشند تا فراخوانی موفق باشد.

## Examples

```js
/* Set logged-in status */
navigator.login.setStatus("logged-in");

/* Set logged-out status */
navigator.login.setStatus("logged-out");
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Federated Credential Management (FedCM) API](/en-US/docs/Web/API/FedCM_API)