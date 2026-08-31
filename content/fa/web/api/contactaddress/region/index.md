---
title: "ContactAddress: region property"
short-title: region
slug: Web/API/ContactAddress/region
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ContactAddress.region
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`region`** در رابط {{domxref("ContactAddress")}} رشته‌ای برمی‌گرداند که شامل بالاترین سطح تقسیمات کشوریِ کشورِ محل آدرس است. این مقدار ممکن است یک ایالت (state)، استان (province)، اوبلاست (oblast) یا بخش (prefecture) باشد.

## مقدار

رشته‌ای که بالاترین سطح تقسیمات کشوری در کشورِ محل آدرس را مشخص می‌کند. این منطقه در کشورهای مختلف نام‌های متفاوتی دارد؛ مانند: state (ایالت)، province (استان)، oblast (اوبلاست)، prefecture (ناحیه) یا county (شهرستان).

## نکات استفاده

در برخی کشورها، مانند بلژیک، معمول نیست که کاربران منطقه را به‌عنوان بخشی از آدرس پستی خود بنویسند. در چنین مواردی، مرورگر مقدار `region` را به‌صورت رشته‌ای خالی برمی‌گرداند. با این حال، آدرس همچنان باید برای هدف مورد نظر (مثلاً ارسال کالا) قابل استفاده باشد. با این وجود، همیشه آدرس‌ها را بررسی کنید تا مطمئن شوید آنچه کاربر ارائه می‌دهد قابل استفاده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}