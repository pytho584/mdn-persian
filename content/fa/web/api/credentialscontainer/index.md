---
title: CredentialsContainer
slug: Web/API/CredentialsContainer
page-type: web-api-interface
browser-compat: api.CredentialsContainer
---

{{APIRef("Credential Management API")}}{{securecontext_header}}

رابط **`CredentialsContainer`** از [Credential Management API](/en-US/docs/Web/API/Credential_Management_API) روش‌هایی را برای درخواست اعتبارنامه‌ها و اطلاع‌رسانی به عامل کاربر هنگام رویدادهایی مانند ورود موفق یا خروج از سیستم ارائه می‌دهد. این رابط از طریق {{domxref('Navigator.credentials')}} در دسترس است.

## ویژگی‌های نمونه

هیچکدام.

## روش‌های نمونه

- {{domxref("CredentialsContainer.create()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک نمونه جدید {{domxref("Credential")}} بر اساس گزینه‌های ارائه‌شده، یا در صورت عدم امکان ایجاد شیء `Credential` با `null` حل می‌شود. در شرایط استثنایی، ممکن است {{jsxref("Promise")}} رد شود.
- {{domxref("CredentialsContainer.get()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با نمونه {{domxref("Credential")}} مطابق با پارامترهای ارائه‌شده حل می‌شود.
- {{domxref("CredentialsContainer.preventSilentAccess()")}}
  - : یک پرچم تنظیم می‌کند که مشخص می‌کند آیا ورود خودکار برای بازدیدهای آینده از مبدأ (origin) فعلی مجاز است یا خیر، سپس یک {{jsxref("Promise")}} خالی برمی‌گرداند. به‌عنوان مثال، ممکن است این روش را پس از خروج کاربر از یک وب‌سایت فراخوانی کنید تا مطمئن شوید که در بازدید بعدی از سایت به‌طور خودکار وارد نمی‌شود. نسخه‌های قدیمی‌تر مشخصات این روش را `requireUserMediation()` می‌نامیدند. برای جزئیات پشتیبانی به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.
- {{domxref("CredentialsContainer.store()")}}
  - : مجموعه‌ای از اعتبارنامه‌ها را برای یک کاربر، درون یک نمونه {{domxref("Credential")}} ارائه‌شده ذخیره می‌کند و آن نمونه را در یک {{jsxref("Promise")}} برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}