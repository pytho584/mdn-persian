---
title: "ContactAddress: addressLine property"
short-title: addressLine
slug: Web/API/ContactAddress/addressLine
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ContactAddress.addressLine
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`addressLine`** از رابط {{domxref("ContactAddress")}}، آرایه‌ای از رشته‌ها است که هر کدام یک خط از آدرس را مشخص می‌کند که توسط هیچ‌کدام از سایر ویژگی‌های `ContactAddress` پوشش داده نشده است. این آرایه ممکن است شامل نام خیابان، شماره پلاک، شماره واحد، مسیر تحویل روستایی، دستورالعمل‌های توصیفی یا صندوق پستی باشد.

## مقدار

آرایه‌ای از رشته‌ها که هر کدام حاوی یک خط از آدرس است. برای مثال، ویژگی `addressLine` برای دفتر Mozilla در لندن دارای ورودی‌های زیر خواهد بود:

| Index | addressLine[] value       |
| ----- | ------------------------- |
| 0     | Metal Box Factory         |
| 1     | Suite 441, 4th floor      |
| 2     | 30 Great Guildford Street |

این‌ها همراه با مقادیر اضافی برای سایر ویژگی‌های {{domxref("ContactAddress")}}، آدرس کامل را نشان می‌دهند که به صورت زیر است:

```plain
Mozilla
Metal Box Factory
Suite 441, 4th floor
30 Great Guildford Street
London SE1 0HS
United Kingdom
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}