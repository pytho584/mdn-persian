---
title: "ProgressEvent: total property"
short-title: total
slug: Web/API/ProgressEvent/total
page-type: web-api-instance-property
browser-compat: api.ProgressEvent.total
---

{{APIRef("XMLHttpRequest API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`ProgressEvent.total`** عددی است که اندازهٔ کل داده‌های در حال انتقال یا پردازش را نشان می‌دهد.

برای رویدادهای `ProgressEvent` که توسط مرورگر ارسال می‌شوند، این مقدار به اندازهٔ منبع بر حسب بایت اشاره دارد و از هدر پاسخ `Content-Length` به دست می‌آید.

در یک `ProgressEvent` که خودتان می‌سازید، این مقدار می‌تواند همچنان مجموع بایت‌های یک منبع باشد؛ هرچند می‌تواند هر عددی نیز باشد.
برای مثال، اگر افشای مقدار دقیق بایت‌های یک منبع برایتان نگران‌کننده است، ممکن است بخواهید `total` را به مقداری مانند `100` یا `1` نرمال‌سازی کنید.
اگر از `1` به‌عنوان مقدار کل استفاده کنید، آنگاه {{domxref("ProgressEvent.loaded")}} یک مقدار اعشاری بین `0` و `1` خواهد بود.

اگر ویژگی {{domxref("ProgressEvent.lengthComputable", "lengthComputable")}} رویداد برابر `false` باشد، این مقدار بی‌معنا است و باید نادیده گرفته شود.

## مقدار

یک عدد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("ProgressEvent")}} که این ویژگی به آن تعلق دارد.