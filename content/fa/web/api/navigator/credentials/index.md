---
title: "Navigator: credentials property"
short-title: credentials
slug: Web/API/Navigator/credentials
page-type: web-api-instance-property
browser-compat: api.Navigator.credentials
---

{{securecontext_header}}{{APIRef("Credential Management API")}}

ویژگی فقط‌خواندنی **`credentials`** در رابط {{domxref("Navigator")}}، شیء {{domxref("CredentialsContainer")}} مرتبط با سند فعلی را بازمی‌گرداند. این شیء روش‌هایی را برای درخواستِ اعتبارنامه (credential) ارائه می‌دهد. همچنین رابط {{domxref("CredentialsContainer")}} زمانی که رویداد مهمی رخ می‌دهد، مانند ورود یا خروج موفق، عامل کاربر (user agent) را مطلع می‌سازد. از این رابط می‌توان برای تشخیص ویژگی (feature detection) استفاده کرد.

## مقدار

یک شیء {{domxref("CredentialsContainer")}}.

## مثال‌ها

```js
if ("credentials" in navigator) {
  navigator.credentials.get({ password: true }).then((creds) => {
    // Do something with the credentials.
  });
} else {
  // Handle sign-in the way you did before.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}