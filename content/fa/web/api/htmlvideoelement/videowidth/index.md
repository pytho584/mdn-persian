---
title: "HTMLVideoElement: videoWidth property"
---

---
title: "HTMLVideoElement: videoWidth property"
short-title: videoWidth
slug: Web/API/HTMLVideoElement/videoWidth
page-type: web-api-instance-property
browser-compat: api.HTMLVideoElement.videoWidth
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`videoWidth`** در رابط {{domxref("HTMLVideoElement")}}، [عرض ذاتی](/en-US/docs/Web/API/HTMLVideoElement/videoHeight#about_intrinsic_width_and_height) ویدیو را بر حسب پیکسل‌های CSS نشان می‌دهد. به زبان ساده، این عرض رسانه در اندازه طبیعی آن است.

برای جزئیات بیشتر، [بخش «درباره عرض و ارتفاع ذاتی» در مستندات `HTMLVideoElement.videoHeight`](/en-US/docs/Web/API/HTMLVideoElement/videoHeight#about_intrinsic_width_and_height) را ببینید.

## مقدار

یک مقدار صحیح که عرض ذاتی ویدیو را بر حسب پیکسل‌های CSS مشخص می‌کند. اگر {{domxref("HTMLMediaElement.readyState", "readyState")}} عنصر برابر با `HTMLMediaElement.HAVE_NOTHING` باشد، مقدار این ویژگی ۰ است، زیرا هنوز اطلاعاتی درباره ابعاد فریم ویدیو یا پوستر در دسترس نیست.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}