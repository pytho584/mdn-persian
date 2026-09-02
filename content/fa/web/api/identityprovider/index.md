---
title: "IdentityProvider"
---

---
title: IdentityProvider
slug: Web/API/IdentityProvider
page-type: web-api-interface
status:
  - experimental
browser-compat: api.IdentityProvider
---

{{APIRef("FedCM API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط **`IdentityProvider`** در [API مدیریت اعتبارنامه‌های فدرال (FedCM)](/en-US/docs/Web/API/FedCM_API) نمایانگر یک {{glossary("Identity provider", "IdP")}} است و دسترسی به اطلاعات و عملکردهای مرتبط را فراهم می‌کند.

{{InheritanceDiagram}}

## متدهای استاتیک

- {{domxref("IdentityProvider.close_static", "close()")}} {{experimental_inline}}
  - : یک سیگنال دستی به مرورگر می‌دهد که جریان ورود به سیستم IdP به پایان رسیده است. برای مثال، این سیگنال برای بستن دیالوگ ورود به سیستم IdP زمانی که ورود به‌طور کامل انجام شده و IdP جمع‌آوری داده‌ها از کاربر را به پایان رسانده است، مورد نیاز است.
- {{domxref("IdentityProvider.getUserInfo_static", "getUserInfo()")}} {{experimental_inline}}
  - : اطلاعات کاربری را که قبلاً وارد سیستم شده است، هنگام بازگشت به یک IdP بازمی‌گرداند. این اطلاعات می‌تواند برای ارائه یک پیام خوش‌آمدگویی و دکمه ورود به سیستم شخصی‌سازی‌شده استفاده شود.

## مثال‌ها

### استفاده پایه از `IdentityProvider.getUserInfo()`

مثال زیر نشان می‌دهد که چگونه می‌توان از متد {{domxref("IdentityProvider.getUserInfo_static", "getUserInfo()")}} برای بازگرداندن اطلاعات کاربری که قبلاً از یک IdP خاص وارد سیستم شده است استفاده کرد.

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

  // Render a personalized sign-in button using the information returned above
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview) در developer.chrome.com (2023)