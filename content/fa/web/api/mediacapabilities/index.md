---
title: MediaCapabilities
slug: Web/API/MediaCapabilities
page-type: web-api-interface
browser-compat: api.MediaCapabilities
---

{{APIRef("Media Capabilities API")}}{{AvailableInWorkers}}

رابط **`MediaCapabilities`** از [Media Capabilities API](/en-US/docs/Web/API/Media_Capabilities_API) اطلاعاتی درباره توانایی‌های رمزگشایی دستگاه، سیستم و مرورگر فراهم می‌کند. این API می‌تواند برای پرس‌وجو از مرورگر درباره توانایی‌های رمزگشایی دستگاه بر اساس کدک‌ها، پروفایل، رزولوشن و نرخ بیت استفاده شود. این اطلاعات می‌توانند برای ارائه جریان‌های رسانه‌ای بهینه به کاربر و تعیین اینکه آیا پخش باید روان و کم‌مصرف باشد، استفاده شوند.

این اطلاعات از طریق ویژگی **`mediaCapabilities`** رابط‌های {{domxref("Navigator")}} و {{domxref("WorkerNavigator")}} قابل دسترسی است.

## روش‌های نمونه

- {{domxref("MediaCapabilities.encodingInfo()")}}
  - : با دریافت یک پیکربندی رسانه‌ای معتبر، یک Promise بازمی‌گرداند که شامل اطلاعاتی درباره پشتیبانی از نوع رسانه و اینکه آیا رمزگذاری چنین رسانه‌ای روان و کم‌مصرف خواهد بود.
- {{domxref("MediaCapabilities.decodingInfo()")}}
  - : با دریافت یک پیکربندی رسانه‌ای معتبر، یک Promise بازمی‌گرداند که شامل اطلاعاتی درباره پشتیبانی از نوع رسانه و اینکه آیا رمزگشایی چنین رسانه‌ای روان و کم‌مصرف خواهد بود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- روش [canPlayType()](/en-US/docs/Web/API/HTMLMediaElement/canPlayType) از [HTMLMediaElement](/en-US/docs/Web/API/HTMLMediaElement)
- روش [isTypeSupported()](/en-US/docs/Web/API/MediaSource/isTypeSupported_static) از [MediaSource](/en-US/docs/Web/API/MediaSource)
- رابط {{domxref("Navigator")}}