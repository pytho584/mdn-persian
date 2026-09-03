---
title: "PaymentAddress: country property"
short-title: country
slug: Web/API/PaymentAddress/country
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentAddress.country
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی فقط‌خواندنی **`country`** از رابط {{domxref('PaymentAddress')}} یک رشته است که کشور آدرس را با استفاده از استاندارد [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) شناسایی می‌کند. این رشته همواره به صورت حروف بزرگ استاندارد خود است.

چند نمونه از مقادیر معتبر `country`: `"US"`، `"GB"`، `"CN"` یا `"JP"`.

## مقدار

یک رشته که شامل کد ISO3166-1 alpha-2 شناسایی‌کننده کشوری است که آدرس در آن قرار دارد، یا یک رشته خالی در صورت عدم وجود کشور، که اغلب می‌توان فرض کرد به معنای «همان کشور مالک سایت» است.

## نکات استفاده

اگر پردازشگر پرداخت آدرس را اعتبارسنجی کند و تشخیص دهد که مقدار `country` نامعتبر است، یک فراخوانی به {{domxref("PaymentRequestUpdateEvent.updateWith()")}} با یک شیء `details` حاوی فیلد `shippingAddressErrors` انجام می‌شود. آن فیلد شامل یک شیء است که ویژگی `country` آن یک رشته است که خطای اعتبارسنجی رخ داده و در صورت امکان، پیشنهادهایی برای رفع آن را نشان می‌دهد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- {{domxref("PaymentRequestUpdateEvent.updateWith")}}