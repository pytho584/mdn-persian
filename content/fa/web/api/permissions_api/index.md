---
title: Permissions API
slug: Web/API/Permissions_API
page-type: web-api-overview
browser-compat:
  - api.Permissions
  - api.Navigator.permissions
  - api.WorkerNavigator.permissions
spec-urls: https://w3c.github.io/permissions/
---

{{DefaultAPISidebar("Permissions API")}}{{AvailableInWorkers}}

**Permissions API** یک روش برنامه‌نویسی یکپارچه برای پرس‌وجوی وضعیت مجوزهای APIِ مرتبط با بافت فعلی، مانند یک صفحه وب یا worker، فراهم می‌کند. برای مثال، می‌توان از آن استفاده کرد تا مشخص شود آیا مجوز دسترسی به یک ویژگی یا API خاص اعطا شده، رد شده، یا به مجوز صریح کاربر نیاز دارد.

## مفاهیم و کاربرد

از نظر تاریخی، APIهای مختلف مجوزهای خود را به‌شکل ناسازگاری مدیریت می‌کردند؛ برای مثال [Notifications API](/en-US/docs/Web/API/Notifications_API) روش‌های خاص خود را برای درخواست مجوز و بررسی وضعیت مجوز داشت، در حالی که [Geolocation API](/en-US/docs/Web/API/Geolocation) چنین نبود. Permissions API ابزارهایی را برای توسعه‌دهندگان فراهم می‌کند تا بتوانند تجربه کاربری یکپارچه‌ای را برای کار با مجوزها پیاده‌سازی کنند.

مجوزهای این API عملاً تمام محدودیت‌های امنیتی بافت را با هم ترکیب می‌کنند؛ از جمله هرگونه الزام برای استفاده از API در بافت امن، محدودیت‌های [Permissions-Policy](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy) اعمال‌شده روی سند، الزامات تعامل با کاربر، و نیاز به نمایش اعلان (prompt) به کاربر. بنابراین، برای مثال، اگر APIای توسط Permissions Policy محدود شده باشد، مجوز بازگشتی `denied` خواهد بود و از کاربر خواسته نمی‌شود دسترسی را تأیید کند.

ویژگی `permissions` روی شیء {{domxref("Navigator")}} در دسترس قرار گرفته است؛ هم در بافت استاندارد مرورگر و هم در بافت worker ({{domxref("WorkerNavigator")}} — بنابراین بررسی مجوزها در داخل workerها نیز ممکن است). این ویژگی یک شیء {{domxref("Permissions")}} بازمی‌گرداند که دسترسی به امکانات Permissions API را فراهم می‌کند.

پس از به‌دست آوردن این شیء، می‌توانید از متد {{domxref("Permissions.query()")}} استفاده کنید تا یک Promise دریافت کنید که برای یک API خاص با {{domxref("PermissionStatus")}} resolve می‌شود.

### درخواست مجوز

اگر وضعیت مجوز `prompt` باشد، کاربر باید برای اعطای دسترسی به ویژگی مورد نظر، یک اعلان (prompt) را تأیید کند.

سازوکاری که این اعلان را فعال می‌کند به API خاص بستگی دارد و به‌عنوان بخشی از Permissions API تعریف نشده است. معمولاً محرک، کدی است که متدی را برای دسترسی به ویژگی یا باز کردن آن فراخوانی می‌کند، یا برای دریافت اعلان‌های مربوط به همان ویژگی ثبت‌نام می‌کند و بعداً به آن دسترسی پیدا خواهد کرد.

توجه داشته باشید که همه ویژگی‌ها به اعلان نیاز ندارند. ممکن است مجوز از طریق یک `Permission Policy`، به‌صورت ضمنی توسط {{glossary("transient activation")}} یا از طریق سازوکار دیگری اعطا شود.

### لغو مجوز

لغو مجوز توسط خود API مدیریت نمی‌شود. به بیان دقیق‌تر، متد {{domxref("Permissions.revoke()")}} پیشنهاد شده بود، اما پس از آن از مرورگرهایی که آن را پیاده‌سازی کرده بودند حذف شد.

کاربران می‌توانند مجوز سایت‌های خاص را به‌صورت دستی از طریق تنظیمات مرورگر حذف کنند:

- **Firefox**: _Hamburger Menu > Settings > Privacy & Security > Permissions_ (سپس دکمه **Settings** را برای مجوز موردنظر انتخاب کنید.)
- **Chrome**: _Hamburger Menu > Settings > Show advanced settings_. در بخش _Privacy_ روی _Content Settings_ کلیک کنید. در کادر محاوره‌ای بازشده، بخش _Location_ را بیابید و گزینه _Ask when a site tries to…_ را انتخاب کنید. در نهایت، روی _Manage Exceptions_ کلیک کنید و مجوزهایی را که به سایت‌های موردنظر داده‌اید حذف کنید.

### APIهای آگاه از مجوز

وضعیت مجوز همه APIها را نمی‌توان با استفاده از Permissions API پرس‌وجو کرد. فهرست غیرجامع APIهای آگاه از مجوز شامل موارد زیر است:

- [Background Synchronization API](/en-US/docs/Web/API/Background_Synchronization_API): `background-sync` (باید همیشه اعطا شود)
- [Clipboard API](/en-US/docs/Web/API/Clipboard_API#security_considerations): `clipboard-read`, `clipboard-write`
- [Compute Pressure API](/en-US/docs/Web/API/Compute_Pressure_API): `compute-pressure`
- [Geolocation API](/en-US/docs/Web/API/Geolocation_API#security_considerations): `geolocation`
- [Local Font Access API](/en-US/docs/Web/API/Local_Font_Access_API): `local-fonts`
- [Local Network Access](/en-US/docs/Web/Security/Defenses/Local_network_access): `local-network`, `loopback-network`. مجوز قدیمی‌تر `local-network-access` همچنان به‌عنوان نام مستعار برای معادل‌های دقیق‌تر پشتیبانی می‌شود.
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API): `microphone`, `camera`
- [Notifications API](/en-US/docs/Web/API/Notifications_API): `notifications`
- [Web-based Payment Handler API](/en-US/docs/Web/API/Web-Based_Payment_Handler_API): `payment-handler`
- [Push API](/en-US/docs/Web/API/Push_API): `push`
- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API): `captured-surface-control`, `display-capture`
- [Screen Wake Lock API](/en-US/docs/Web/API/Screen_Wake_Lock_API): `screen-wake-lock`
- [Sensor APIs](/en-US/docs/Web/API/Sensor_APIs): `accelerometer`, `gyroscope`, `magnetometer`, `ambient-light-sensor`
- [Storage Access API](/en-US/docs/Web/API/Storage_Access_API): `storage-access`, `top-level-storage-access`
- [Storage API](/en-US/docs/Web/API/Storage_API): `persistent-storage`
- [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API): `bluetooth`
- [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API): `midi`
- [Window Management API](/en-US/docs/Web/API/Window_Management_API): `window-management`

## رابط‌ها

- {{domxref("Permissions")}}
  - : عملکرد اصلی Permissions API، مانند متدهایی برای پرس‌وجو و لغو مجوزها را فراهم می‌کند.
- {{domxref("PermissionStatus")}}
  - : به وضعیت فعلی یک مجوز دسترسی می‌دهد و یک مدیریت‌کننده رویداد (event handler) برای واکنش به تغییرات وضعیت مجوز ارائه می‌کند.

### افزونه‌های سایر رابط‌ها

- {{domxref("Navigator.permissions")}} و {{domxref("WorkerNavigator.permissions")}} {{ReadOnlyInline}}
  - : به ترتیب از بافت اصلی و بافت worker به شیء {{domxref("Permissions")}} دسترسی می‌دهند.

## مثال‌ها

ما نمونه‌ای به نام Location Finder ایجاد کرده‌ایم. می‌توانید [مثال را به‌صورت زنده اجرا کنید](https://chrisdavidmills.github.io/location-finder-permissions-api/)، [کد منبع آن را در GitHub مشاهده کنید](https://github.com/chrisdavidmills/location-finder-permissions-api/tree/gh-pages)، یا درباره نحوه کار آن در مقاله [استفاده از Permissions API](/en-US/docs/Web/API/Permissions_API/Using_the_Permissions_API) بیشتر بخوانید.

مثال [`Permissions.query()`](/en-US/docs/Web/API/Permissions/query#test_support_for_various_permissions) همچنین کدی را نشان می‌دهد که اکثر مجوزها را در مرورگر فعلی آزمایش و نتیجه را ثبت (log) می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- [استفاده از Permissions API](/en-US/docs/Web/API/Permissions_API/Using_the_Permissions_API)
- [استفاده از Permissions API برای تشخیص اینکه کاربران چند وقت یکبار دسترسی به دوربین را مجاز یا رد می‌کنند](https://blog.addpipe.com/using-permissions-api-to-detect-getusermedia-responses/)
- {{DOMxref("Notification.permission_static", "Notification.permission")}}
- [حریم خصوصی، مجوزها و امنیت اطلاعات](/en-US/docs/Web/Privacy)