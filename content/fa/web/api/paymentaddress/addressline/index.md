---
title: "PaymentAddress: addressLine property"
short-title: addressLine
slug: Web/API/PaymentAddress/addressLine
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentAddress.addressLine
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

خاصیت فقط-خواندنی **`addressLine``** از رابط {{domxref('PaymentAddress')}} یک آرایه از رشته‌ها است که هر کدام یک خط از آدرس را مشخص می‌کند که توسط سایر ویژگی‌های `PaymentAddress` پوشش داده نشده است.

این خطوط ممکن است شامل نام خیابان، شماره ساختمان، شماره آپارتمان، مسیر تحویل روستایی، توضیحات راهنما، یا صندوق پستی باشند.

## مقدار

یک آرایه از رشته‌ها که هر کدام حاوی یک خط از آدرس است. برای مثال، آرایه `addressLine` برای فضای Mozilla در لندن شامل ورودی‌های زیر خواهد بود:

| ایندکس | مقدار addressLine[] |
|--------|---------------------|
| 0      | Metal Box Factory   |
| 1      | Suite 441, 4th floor|
| 2      | 30 Great Guildford Street |

این‌ها، همراه با مقادیر اضافی برای سایر ویژگی‌های {{domxref("PaymentAddress")}}، آدرس کامل را نشان می‌دهند که عبارت است از:

Mozilla  
Metal Box Factory  
Suite 441, 4th floor  
30 Great Guildford Street  
London SE1 0HS  
United Kingdom

## سازگاری با مرورگر

{{Compat}}