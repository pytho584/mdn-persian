---
title: "AuthenticatorAttestationResponse: getTransports() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAttestationResponse/getTransports"
translated_by: "n8n + AI"
short-title: getTransports()
slug: Web/API/AuthenticatorAttestationResponse/getTransports
page-type: web-api-instance-method
browser-compat: api.AuthenticatorAttestationResponse.getTransports
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد **`getTransports()`** از رابط {{domxref("AuthenticatorAttestationResponse")}} یک آرایه از رشته‌ها را برمی‌گرداند که حمل‌ونقل‌های مختلفی را که ممکن است توسط احرازکننده استفاده شوند، توصیف می‌کند.

این حمل‌ونقل‌ها ممکن است USB، NFC، BLE، داخلی (زمانی که احرازکننده از دستگاه قابل حذف نیست) یا یک رویکرد ترکیبی باشند. سایت‌ها نباید این آرایه را تفسیر کنند، بلکه باید آن را همراه با بقیه اطلاعات اعتبارنامه ذخیره کنند. در یک فراخوانی بعدی {{domxref("CredentialsContainer.get()", "navigator.credentials.get()")}}، مقدار(های) `transports` مشخص شده در داخل `publicKey.allowCredentials` باید به مقدار آرایه ذخیره شده تنظیم شوند. این یک نکته به مرورگر می‌دهد که هنگام تأیید این اعتبارنامه، چه نوع احرازکننده‌هایی را امتحان کند.

## Syntax

```js-nolint
getTransports()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Array")}} از رشته‌ها که نشان‌دهنده حمل‌ونقل‌های مختلف پشتیبانی شده توسط احرازکننده است، به ترتیب لغت‌نامه. مقادیر ممکن است شامل موارد زیر باشند:

- `"ble"`
  - : احرازکننده ممکن است از طریق [BLE (Bluetooth Low Energy)](https://en.wikipedia.org/wiki/Bluetooth_Low_Energy) استفاده شود.
- `"hybrid"`
  - : احرازکننده می‌تواند از طریق ترکیبی از مکانیسم‌های حمل‌ونقل داده و مجاورت (اغلب مجزا) استفاده شود. این به عنوان مثال، احراز هویت در رایانه رومیزی با استفاده از تلفن هوشمند را پشتیبانی می‌کند.
- `"internal"`
  - : احرازکننده به طور خاص به دستگاه سرویس‌گیرنده متصل است (قابل حذف نیست).
- `"nfc"`
  - : احرازکننده ممکن است از طریق [NFC (Near Field Communication)](https://en.wikipedia.org/wiki/Near-field_communication) استفاده شود.
- `"usb"`
  - : احرازکننده می‌تواند از طریق USB مورد ارتباط قرار گیرد.

## مثال‌ها

برای یک مثال دقیق به [ایجاد یک اعتبارنامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/create#creating_a_public_key_credential) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}