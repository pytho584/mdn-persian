---
title: "Navigator: deviceMemory property"
short-title: deviceMemory
slug: Web/API/Navigator/deviceMemory
page-type: web-api-instance-property
browser-compat: api.Navigator.deviceMemory
---

{{APIRef("Device Memory API")}}{{securecontext_header}}

خاصیت فقط‌خواندنی **`deviceMemory`** در رابط {{domxref("Navigator")}} مقدار تقریبی حافظه دستگاه را بر حسب گیگابایت برمی‌گرداند.

مقدار گزارش‌شده عمداً نادقیق است تا {{glossary("fingerprinting")}} محدود شود.
این مقدار با گرد کردن حافظه واقعی به نزدیک‌ترین توان ۲ و سپس تقسیم آن عدد بر ۱۰۲۴ تقریب زده می‌شود.
سپس برای محافظت از حریم خصوصیِ دارندگان دستگاه‌های با حافظه خیلی کم یا خیلی زیاد، در حد پایین و بالایی محدود می‌شود.
این حدود ممکن است در طول زمان تغییر کند (به [جدول سازگاری مرورگر](#browser_compatibility) مراجعه کنید).

## مقدار

یک عدد اعشاری که به مقدار توان ۲ گرد شده و به محدوده‌های تعیین‌شده توسط پیاده‌سازی محدود شده است.

برای مثال، اگر مرورگری مقادیر کمتر از `2` یا بیشتر از `32` را گزارش نکند، مقدار یکی از این‌ها خواهد بود: `2`، `4`، `8`، `16`، `32`.

## مثال‌ها

```js
const memory = navigator.deviceMemory;
console.log(`This device approximately ${memory}GiB of RAM.`);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- هدر HTTP {{HTTPHeader("Sec-CH-Device-Memory")}}