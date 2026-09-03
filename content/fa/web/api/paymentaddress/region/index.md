---
title: "PaymentAddress: region property"
short-title: region
slug: Web/API/PaymentAddress/region
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentAddress.region
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی فقط‌خواندنی **`region`** از رابط {{domxref('PaymentAddress')}} رشته‌ای را بازمی‌گرداند که شامل بالاترین سطح تقسیمات کشوری در کشورِ محلِ قرارگیری آدرس است. برای نمونه، این مقدار ممکن است یک ایالت (state)، استان (province)، اوبلاست (oblast) یا پریفکتور (prefecture) باشد.

## مقدار

یک رشته که بالاترین سطح تقسیمات اداری در کشورِ محلِ آدرس را مشخص می‌کند. این ناحیه در کشورهای مختلف نام‌های گوناگونی دارد؛ مانند: ایالت (state)، استان (province)، اوبلاست (oblast)، پریفکتور (prefecture) یا کانتی (county).

## نکات استفاده

در برخی کشورها مانند بلژیک، معمول نیست که افراد منطقه (region) را به‌عنوان بخشی از آدرس پستی خود وارد کنند. در چنین مواردی، مرورگر مقدار `region` را یک رشتهٔ خالی بازمی‌گرداند. با این حال، چنین آدرسی همچنان باید برای هدف موردنظر (مثلاً ارسال یک محصول) قابل قبول باشد. در هر صورت، همیشه آدرس‌ها را بررسی کنید تا مطمئن شوید آنچه کاربر ارائه کرده است قابل استفاده است.

## سازگاری مرورگر

{{Compat}}