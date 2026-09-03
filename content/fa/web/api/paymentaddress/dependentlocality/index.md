---
title: "PaymentAddress: dependentLocality property"
---

---
title: "PaymentAddress: dependentLocality property"
short-title: dependentLocality
slug: Web/API/PaymentAddress/dependentLocality
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentAddress.dependentLocality
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی فقط‌خواندنی **`dependentLocality`** از رابط {{domxref('PaymentAddress')}} رشته‌ای (string) است که شامل نام زیرمحله‌ای (sublocality) درون یک شهر می‌شود؛ مانند محله (neighborhood)، ناحیهٔ شهری (borough)، منطقه (district) یا در بریتانیا، محلهٔ وابسته (dependent locality). این ویژگی با نام _post town_ (شهر پستی) نیز شناخته می‌شود.

## Value

رشته‌ای که بخش زیرمحلهٔ آدرس را نشان می‌دهد. اگر زیرمحله‌ای در دسترس نباشد یا به آن نیازی نباشد، این مقدار ممکن است یک رشتهٔ خالی باشد. از این ویژگی برای رفع ابهام استفاده می‌شود؛ زمانی که شهری ممکن است مناطقی داشته باشد که نام خیابان‌ها در آن‌ها تکراری است.

زیرمحله، ناحیه‌ای درون یک شهر است؛ مانند محله، ناحیهٔ شهری یا منطقه. در بریتانیا، از این ویژگی برای اشاره به **post town** (شهر پستی) استفاده می‌شود؛ اصطلاحی که رویال میل (Royal Mail) رسماً آن را **dependent locality** (محلهٔ وابسته) می‌نامد. این یک ویژگی ابهام‌زدا برای آدرس‌ها در مکان‌هایی است که شهری ممکن است مناطقی با نام خیابان‌های تکراری داشته باشد.

## Browser compatibility

{{Compat}}