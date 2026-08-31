---
title: "AuthenticatorAssertionResponse: userHandle property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAssertionResponse/userHandle"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAssertionResponse: userHandle property"
short-title: userHandle
slug: Web/API/AuthenticatorAssertionResponse/userHandle
page-type: web-api-instance-property
browser-compat: api.AuthenticatorAssertionResponse.userHandle
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`userHandle`** از رابط {{domxref("AuthenticatorAssertionResponse")}} یک شیء {{jsxref("ArrayBuffer")}} است که یک شناسه‌ی مبهم (opaque) برای کاربر معین فراهم می‌کند. چنین شناسه‌ای را سرور طرف تکیه‌کننده می‌تواند برای پیوند دادن حساب کاربر با اعتبارنامه‌ها و سایر داده‌های متناظر آن استفاده کند.

این مقدار به‌عنوان `user.id` در گزینه‌های ارسال‌شده به فراخوانی اولیه {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} مشخص می‌شود.

## مقدار

یک شیء {{jsxref("ArrayBuffer")}} که نمایانگر شناسه‌ای برای کاربر فعلی است. این مقدار برای خواندن انسان در نظر گرفته نشده است. طرف تکیه‌کننده باید اطمینان حاصل کند که `user.id` ارسال‌شده به فراخوانی اولیه `create()` حاوی **هیچ** اطلاعات شناسایی شخصی (مانند نام کاربری، ایمیل یا شماره تلفن) نباشد.

برای فراخوانی‌های {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} که با ویژگی غیرخالی `allowCredentials` انجام می‌شوند، `userHandle` بازگشتی ممکن است null باشد.

## مثال‌ها

برای یک مثال دقیق، [بازیابی یک اعتبار کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/get#retrieving_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CredentialsContainer.create()")}} که مقدار این ویژگی را تعیین می‌کند