---
title: "IdentityProvider: getUserInfo() static method"
short-title: getUserInfo()
slug: Web/API/IdentityProvider/getUserInfo_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.IdentityProvider.getUserInfo_static
---

{{APIRef("FedCM API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد ایستای **`getUserInfo()`** از رابط {{domxref("IdentityProvider")}} اطلاعات مربوط به کاربری را که وارد سامانه شده است بازمی‌گرداند؛ این اطلاعات می‌تواند برای ارائهٔ پیام خوش‌آمدگویی و دکمهٔ ورود شخصی‌سازی‌شده استفاده شود. این متد باید از درون یک {{htmlelement("iframe")}} متعلق به مبدأ (origin) {{glossary("Identity provider", "IdP")}} فراخوانی شود تا اسکریپت‌های {{glossary("Relying party", "relying party")}} (RP) نتوانند به داده‌ها دسترسی پیدا کنند. این کار باید پس از ورود کاربر به یک سایت RP انجام شود.

این الگو در سایت‌هایی که برای ورود از فدراسیون هویت استفاده می‌کنند، از قبل رایج است؛ اما `getUserInfo()` راهی برای رسیدن به آن بدون اتکا به [کوکی‌های شخص ثالث](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) فراهم می‌کند.

## سینتکس

```js-nolint
IdentityProvider.getUserInfo(config)
```

### پارامترها

- `config`
  - : یک شیء پیکربندی که می‌تواند ویژگی‌های زیر را شامل شود:
    - `configURL`
      - : نشانی URL [فایل پیکربندی](/en-US/docs/Web/API/FedCM_API/IDP_integration#provide_a_config_file_and_endpoints) برای ارائه‌دهنده هویتی است که می‌خواهید اطلاعات کاربر را از آن دریافت کنید.
    - `clientId`
      - : شناسه کلاینت RP که توسط IdP صادر شده است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از اشیاء تکمیل می‌شود و هر شیء شامل اطلاعاتی است که یک حساب کاربری جداگانه را نشان می‌دهد. هر شیء شامل ویژگی‌های زیر است:

- `email`
  - : رشته‌ای که نشانی ایمیل کاربر را نشان می‌دهد.
- `name`
  - : رشته‌ای که نام کامل کاربر را نشان می‌دهد.
- `givenName`
  - : رشته‌ای که نام کوچک (نام مستعار یا مخفف) کاربر را نشان می‌دهد.
- `picture`
  - : رشته‌ای که نشانی URL تصویر پروفایل کاربر را نشان می‌دهد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `configURL` ارائه‌شده نامعتبر باشد یا مبدأ سند جاسازی‌شده با `configURL` مطابقت نداشته باشد، پرتاب می‌شود.
- `NetworkError` {{domxref("DOMException")}}
  - : اگر مرورگر نتواند به IdP متصل شود یا `getUserInfo()` از سند سطح بالا فراخوانی شود، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر `<iframe>` جاسازی‌کننده دارای {{httpheader("Permissions-Policy/identity-credentials-get", "identity-credentials-get")}} [Permissions-Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) به‌گونه‌ای تنظیم نشده باشد که استفاده از `getUserInfo()` را مجاز کند، یا اگر FedCM API به‌طور سراسری توسط خط‌مشی‌ای که روی سند سطح بالا تنظیم شده غیرفعال شده باشد، پرتاب می‌شود.

## توضیحات

هنگامی که `getUserInfo()` فراخوانی می‌شود، مرورگر تنها در صورتی که هر دو شرط زیر برقرار باشند، درخواستی به [endpoint فهرست حساب‌ها](/en-US/docs/Web/API/FedCM_API/IDP_integration#the_accounts_list_endpoint) IdP مشخص‌شده برای دریافت اطلاعات کاربر ارسال می‌کند:

- کاربر قبلاً از طریق FedCM در همان نمونه مرورگر با IdP به RP وارد شده باشد و داده‌ها پاک نشده باشند.
- کاربر در همان نمونه مرورگر به IdP وارد شده باشد.

`getUserInfo()` باید از درون یک `<iframe>` جاسازی‌شده فراخوانی شود و مبدأ سایت جاسازی‌شده باید با `configURL` مربوط به IdP مطابقت داشته باشد. علاوه بر این، HTML جاسازی‌کننده باید به‌طور صریح استفاده از آن را از طریق {{httpheader("Permissions-Policy/identity-credentials-get", "identity-credentials-get")}} [Permissions-Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مجاز کند:

```html
<iframe
  src="https://idp.example/signin"
  allow="identity-credentials-get"></iframe>
```

## مثال‌ها

### استفادهٔ پایه از `IdentityProvider.getUserInfo()`

مثال زیر نشان می‌دهد که چگونه می‌توان از متد `IdentityProvider.getUserInfo()` برای بازگرداندن اطلاعات کاربری که قبلاً از یک IdP خاص وارد شده استفاده کرد.

```js
// Iframe displaying a page from the https://idp.example origin
const userInfo = await IdentityProvider.getUserInfo({
  configURL: "https://idp.example/fedcm.json",
  clientId: "client1234",
});

// IdentityProvider.getUserInfo() returns an array of user information.
if (userInfo.length > 0) {
  // Returning accounts should be first, so the first account received
  // is guaranteed to be a returning account
  const name = userInfo[0].name;
  const givenName = userInfo[0].given_name;
  const displayName = givenName || name;
  const picture = userInfo[0].picture;
  const email = userInfo[0].email;

  // …

  // Render the personalized sign-in button using the information above
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview) در developer.chrome.com (۲۰۲۳)