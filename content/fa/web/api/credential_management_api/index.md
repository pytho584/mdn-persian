---
title: Credential Management API
slug: Web/API/Credential_Management_API
page-type: web-api-overview
browser-compat:
  - api.Credential
  - api.CredentialsContainer
  - api.FederatedCredential
  - api.PasswordCredential
spec-urls: https://w3c.github.io/webappsec-credential-management/
---

{{DefaultAPISidebar("Credential Management API")}}{{securecontext_header}}

API مدیریت اعتبارنامه (Credential Management API) به وب‌سایت‌ها امکان می‌دهد اعتبارنامه‌ها ({{glossary("credential", "credentials")}}) را ایجاد، ذخیره و بازیابی کنند. اعتبارنامه موردی است که سیستم را قادر می‌سازد تصمیم {{glossary("authentication")}} بگیرد؛ برای مثال، اینکه آیا کاربر را به حساب کاربری وارد کند یا نه. می‌توان آن را به‌عنوان مدرکی در نظر گرفت که کاربر به وب‌سایت ارائه می‌کند تا ثابت کند واقعاً همان شخصی است که ادعا می‌کند.

## مفاهیم و کاربرد

رابط اصلی {{domxref("CredentialsContainer")}} است که از طریق ویژگی {{domxref("navigator.credentials")}} در دسترس قرار می‌گیرد و سه عملکرد اصلی را ارائه می‌دهد:

- {{domxref("CredentialsContainer.create", "create()")}}: ایجاد یک اعتبارنامه جدید.
- {{domxref("CredentialsContainer.store", "store()")}}: ذخیره‌سازی یک اعتبارنامه جدید به‌صورت محلی.
- {{domxref("CredentialsContainer.get", "get()")}}: بازیابی یک اعتبارنامه که سپس می‌توان از آن برای ورود کاربر استفاده کرد.

این API از چهار نوع مختلف اعتبارنامه پشتیبانی می‌کند که همگی به‌صورت زیرکلاس‌هایی از {{domxref("Credential")}} نمایش داده می‌شوند:

| نوع | رابط |
| ----------------------- | ---------------------------------------------------------------------------------- |
| گذرواژه | {{domxref("PasswordCredential")}} |
| هویت فدرال | {{domxref("IdentityCredential")}}, {{domxref("FederatedCredential")}} (منسوخ) |
| رمز یک‌بارمصرف (OTP) | {{domxref("OTPCredential")}} |
| احراز هویت وب | {{domxref("PublicKeyCredential")}} |

صفحه راهنمای [انواع اعتبارنامه](/en-US/docs/Web/API/Credential_Management_API/Credential_types) مروری بر انواع مختلف اعتبارنامه‌ها و نحوه استفاده از آن‌ها ارائه می‌دهد.

## رابط‌ها

- {{domxref("Credential")}}
  - : اطلاعاتی درباره یک موجودیت (entity) به‌عنوان پیش‌شرط تصمیم اعتماد فراهم می‌کند.
- {{domxref("CredentialsContainer")}}
  - : روش‌هایی را برای درخواست اعتبارنامه‌ها ارائه می‌دهد و هنگام وقوع رویدادهای مهم مانند ورود یا خروج موفق، عامل کاربر (user agent) را مطلع می‌کند. این رابط از طریق `navigator.credentials` قابل دسترسی است.
- {{domxref("FederatedCredential")}}
  - : اطلاعاتی درباره اعتبارنامه‌های یک تأمین‌کننده هویت فدرال (federated identity provider) فراهم می‌کند؛ تأمین‌کننده‌ای که وب‌سایت به آن اعتماد دارد تا کاربر را به‌درستی احراز هویت کند و API را برای این منظور ارائه می‌دهد. [OpenID Connect](https://openid.net/developers/specs/) نمونه‌ای از چنین چارچوبی است.
- {{domxref("PasswordCredential")}}
  - : اطلاعاتی درباره یک جفت نام کاربری/گذرواژه فراهم می‌کند.

### افزونه‌هایی برای سایر رابط‌ها

- {{domxref("Navigator.credentials")}} {{ReadOnlyInline}}
  - : رابط {{domxref("CredentialsContainer")}} را برمی‌گرداند که روش‌هایی را برای درخواست اعتبارنامه‌ها و مطلع کردن عامل کاربر هنگام وقوع رویدادهای مهم مانند ورود یا خروج موفق ارائه می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Web Authentication API", "", "", "nocode")}}
- {{domxref("WebOTP API", "", "", "nocode")}}
- {{domxref("FedCM API", "Federated Credential Management (FedCM) API", "", "nocode")}}