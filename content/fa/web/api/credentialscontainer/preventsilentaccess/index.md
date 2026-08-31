---
title: "CredentialsContainer: preventSilentAccess() method"
short-title: preventSilentAccess()
slug: Web/API/CredentialsContainer/preventSilentAccess
page-type: web-api-instance-method
browser-compat: api.CredentialsContainer.preventSilentAccess
---

{{APIRef("Credential Management API")}}{{SecureContext_Header}}

متد **`preventSilentAccess()`** از رابط {{domxref("CredentialsContainer")}} یک پرچم تنظیم می‌کند که مشخص می‌کند آیا ورود خودکار برای بازدیدهای آینده از مبدأ فعلی مجاز است یا خیر، سپس یک {{jsxref("Promise")}} برمی‌گرداند که به `undefined` تبدیل می‌شود. برای مثال، ممکن است پس از خروج کاربر از یک وب‌سایت، این متد را فراخوانی کنید تا مطمئن شوید که در بازدید بعدی از سایت به‌طور خودکار وارد نشود. میانجی‌گری (mediation) بسته به مبدأ متفاوت است و یک نقطه بررسی اضافی برای اعتبارنامه‌های ذخیره‌شده در مرورگر است که وضعیت ورود حساب کاربر را به کاربر اطلاع می‌دهد. این متد معمولاً پس از خروج کاربر از یک وب‌سایت فراخوانی می‌شود تا اطمینان حاصل شود که اطلاعات ورود کاربر در بازدید بعدی از سایت به‌طور خودکار منتقل نمی‌شود.

هنگام استفاده از {{domxref("PublicKeyCredential")}}، این متد معمولاً تأثیری ندارد؛ چنین تأییدکننده‌هایی معمولاً نیاز به تعامل کاربر دارند. با این حال، _ممکن است_ برخی تأییدکننده‌های خاص که در غیر این صورت می‌توانستند به‌صورت بی‌صدا عمل کنند، از کار بیفتند.

نسخه‌های قبلی مشخصات، این متد را `requireUserMediation()` می‌نامیدند. بخش [سازگاری با مرورگرها](/fa/docs/Web/API/CredentialsContainer#browser_compatibility) جزئیات پشتیبانی را دارد.

## نحو

```js-nolint
preventSilentAccess()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به `undefined` تبدیل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}