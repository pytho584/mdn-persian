---
title: MediaKeySystemAccess
slug: Web/API/MediaKeySystemAccess
page-type: web-api-interface
browser-compat: api.MediaKeySystemAccess
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

رابط **`MediaKeySystemAccess`** از [API افزونه‌های رسانه‌ای رمزگذاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) دسترسی به یک سیستم کلید برای رمزگشایی و/یا یک ارائه‌دهنده حفاظت از محتوا را فراهم می‌کند. شما می‌توانید با استفاده از متد {{domxref("Navigator.requestMediaKeySystemAccess","Navigator.requestMediaKeySystemAccess()")}} یک نمونه از این شیء را درخواست کنید.

## ویژگی‌های نمونه

- {{domxref("MediaKeySystemAccess.keySystem")}} {{ReadOnlyInline}}
  - : یک رشته که سیستم کلید در حال استفاده را شناسایی می‌کند بازمی‌گرداند.

## روش‌های نمونه

- {{domxref("MediaKeySystemAccess.createMediaKeys()")}}
  - : یک {{jsxref('Promise')}} بازمی‌گرداند که به یک شیء جدید {{domxref("MediaKeys")}} حل می‌شود.
- {{domxref("MediaKeySystemAccess.getConfiguration()")}}
  - : یک شیء با ترکیب پشتیبانی‌شده از گزینه‌های پیکربندی بازمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}