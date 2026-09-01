---
title: Federated Credential Management (FedCM) API
slug: Web/API/FedCM_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.IdentityCredential
---

{{SeeCompatTable}}{{DefaultAPISidebar("FedCM API")}}

**API مدیریت اعتبارنامه فدرال (یا _FedCM API_)** یک مکانیسم استاندارد برای {{glossary("Identity provider", "identity providers")}} (IdP) فراهم می‌کند تا خدمات فدراسیون هویت را در وب به‌صورت حفظ‌کننده حریم خصوصی و بدون نیاز به [کوکی‌های شخص ثالث](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) و تغییر مسیرها در دسترس قرار دهند. این شامل یک API جاوااسکریپت است که استفاده از احراز هویت فدرال را برای فعالیت‌هایی مانند ورود یا ثبت‌نام در یک وب‌سایت امکان‌پذیر می‌سازد.

## مفاهیم FedCM

فدراسیون هویت به معنای واگذاری احراز هویت کاربر از یک وب‌سایت که نیاز به ثبت‌نام یا ورود کاربر دارد (مانند یک سایت تجارت الکترونیک یا شبکه اجتماعی، که به آن {{glossary("Relying party", "relying party")}} یا RP نیز گفته می‌شود) به یک تأمین‌کننده هویت شخص ثالث قابل اعتماد (IdP) مانند Google، Facebook/Meta، GitHub و غیره است.

طرف‌های متکی (RP) می‌توانند با IdP‌ها ادغام شوند و به کاربران اجازه دهند با استفاده از حساب‌هایی که در IdP ثبت کرده‌اند وارد شوند. فدراسیون هویت از طریق مجموعه کوچکی از IdP‌های اختصاصی، احراز هویت وب را از نظر امنیت، اعتماد مصرف‌کننده و تجربه کاربری بهبود بخشیده است، در مقایسه با اینکه هر سایت نیازهای ورود خود را با نام‌کاربری و رمزعبور جداگانه مدیریت کند.

مشکل این است که فدراسیون هویت سنتی به {{htmlelement("iframe")}}ها، تغییر مسیرها و کوکی‌های شخص ثالث متکی است که برای ردیابی شخص ثالث نیز استفاده می‌شوند. مرورگرها در تلاش برای حفظ حریم خصوصی کاربران، استفاده از این ویژگی‌ها را محدود می‌کنند، اما یک عارضه جانبی آن این است که استفاده‌های معتبر و غیرردیابی را نیز دشوارتر می‌کند، که شامل فدراسیون هویت می‌شود.

این امر بر ورود فدرال به طور کلی و همچنین موارد استفاده خاص‌تر فدراسیون هویت تأثیر می‌گذارد:

- [خروج از سیستم از طریق کانال جلویی OIDC](https://openid.net/specs/openid-connect-frontchannel-1_0.html): این جریان نیازمند جاسازی چندین `<iframe>` RP توسط IdP است که به کوکی‌های RP وابسته هستند.
- ویجت‌های اجتماعی: برای ارائه ویجت‌های اجتماعی، کوکی شخص ثالث IdP باید از مبدأ سطح بالای RP ارائه شود.
- دکمه‌های شخصی‌سازی شده: نمایش اطلاعات ورود شخصی‌سازی شده روی یک {{htmlelement("button")}} در مبدأ RP به صورت یک `<iframe>` IdP پیاده‌سازی می‌شود که به کوکی‌های شخص ثالث نیاز دارد.
- بازنشانی جلسه بدون پیمایش سطح بالا یا پنجره‌های بازشو.

هدف FedCM دور زدن این مشکل است، با ارائه یک مکانیسم اختصاصی برای جریان‌های هویت فدرال در وب و امکان‌پذیر ساختن مرورگرهای پشتیبان برای ارائه عناصر رابط کاربری ویژه در RP‌ها، تا کاربران بتوانند یک حساب IdP را برای ورود انتخاب کنند.

استفاده از API FedCM شامل دو بخش است که در راهنماهای مرتبط زیر پوشش داده شده‌اند:

1. [ادغام IdP با FedCM](/en-US/docs/Web/API/FedCM_API/IDP_integration) — آنچه یک تأمین‌کننده هویت باید ارائه دهد تا یک RP بتواند با آن ادغام شود.
2. [ورود فدرال RP](/en-US/docs/Web/API/FedCM_API/RP_sign-in) — قابلیت‌های FedCM که یک RP برای ورود کاربر با استفاده از حساب IdP خود نیاز دارد. یک درخواست ورود FedCM با استفاده از متد {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} آغاز می‌شود.

> [!NOTE]
> [Google Sign In](https://developers.google.com/identity/gsi/web/guides/overview) نمونه‌ای از یک IdP است که از FedCM پشتیبانی می‌کند. [Migrate to FedCM](https://developers.google.com/identity/gsi/web/guides/fedcm-migration) دستورالعمل‌هایی را برای RPهایی که مایل به مهاجرت برنامه‌های موجود با استفاده از Google Sign In به ورود فدرال هستند، ارائه می‌دهد.

## ادغام خط مشی مجوزها و پشتیبانی از `<iframe>`

{{httpheader("Permissions-Policy/identity-credentials-get", "identity-credentials-get")}} [Permissions-Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) می‌تواند برای کنترل مجوز استفاده از FedCM استفاده شود. به طور خاص، استفاده از روش‌های زیر را مجاز می‌کند:

- {{domxref("CredentialsContainer.get()")}}
- {{domxref("IdentityCredential.disconnect_static", "IdentityCredential.disconnect()")}}
- {{domxref("IdentityProvider.getUserInfo_static", "IdentityProvider.getUserInfo()")}}

توسعه‌دهندگان می‌توانند به طور صریح با استفاده از ویژگی `allow` به یک {{htmlelement("iframe")}} اجازه استفاده از FedCM را بدهند:

```html
<iframe src="3rd-party.example" allow="identity-credentials-get"></iframe>
```

در دسترس بودن FedCM درون `<iframe>`ها چند مورد استفاده را امکان‌پذیر می‌کند:

- سایت‌های بزرگتر نمی‌خواهند یک اسکریپت ورود شخص ثالث کنترل فریم سطح بالا را به دست گیرد؛ در عوض آنها می‌خواهند آن اسکریپت را اضافه کرده و FedCM را از درون یک {{htmlelement("iframe")}} فراخوانی کنند.
- برخی `<iframe>`ها ممکن است خود به احراز هویت فدرال نیاز داشته باشند.

## رابط‌ها

- {{domxref("IdentityCredential")}}
  - : نشان‌دهنده یک اعتبارنامه هویت کاربر است که از احراز هویت فدرال موفق حاصل می‌شود. یک فراخوانی موفق {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} که شامل گزینه `identity` باشد، با یک نمونه {{domxref("IdentityCredential")}} تکمیل می‌شود.
- {{domxref("IdentityCredentialError")}}
  - : نشان‌دهنده یک خطای احراز هویت است که نشان می‌دهد عامل کاربر پس از درخواست کاربر برای احراز هویت با استفاده از یک اعتبارنامه فدرال، یک تأییدیه هویت دریافت نکرده است.
- {{domxref("IdentityProvider")}}
  - : نشان‌دهنده یک IdP است و دسترسی به اطلاعات و قابلیت‌های مرتبط را فراهم می‌کند.
- {{domxref("NavigatorLogin")}}
  - : قابلیت ورود برای IdP‌ها را تعریف می‌کند، از جمله متد {{domxref("NavigatorLogin.setStatus", "Navigator.login.setStatus()")}} برای [به‌روزرسانی وضعیت ورود IdP](/en-US/docs/Web/API/FedCM_API/IDP_integration#update_login_status_using_the_login_status_api).

## افزونه‌هایی به سایر رابط‌ها

- {{domxref("CredentialsContainer.get()")}}, گزینه `identity`
  - : `identity` یک شی حاوی جزئیات IdP‌های فدرال است که یک وب‌سایت طرف متکی (RP) می‌تواند برای ورود کاربران استفاده کند. این باعث می‌شود که یک فراخوانی `get()` یک درخواست برای ورود کاربر به یک RP با یک IdP را آغاز کند.
- {{domxref("Navigator.login")}}
  - : دسترسی به شی {{domxref("NavigatorLogin")}} مرورگر را فراهم می‌کند.

## سرآیندهای HTTP

- {{httpheader("Set-Login")}}
  - : یک مکانیسم HTTP برای [به‌روزرسانی وضعیت ورود](/en-US/docs/Web/API/FedCM_API/IDP_integration#update_login_status_using_the_login_status_api) از طریق HTTP فراهم می‌کند.

## مثال‌ها

برای مثال‌های کد، مراجعه کنید:

- [Implement an identity solution with FedCM on the Identity Provider side](https://developer.chrome.com/docs/identity/fedcm/implement/identity-provider) در developer.chrome.com (2025)
- [Implement an identity solution with FedCM on the Relying Party side](https://developer.chrome.com/docs/identity/fedcm/implement/relying-party) در developer.chrome.com (2025)

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- [Federated Credential Management API](https://developer.chrome.com/docs/identity/fedcm/overview)