---
title: "Device orientation events"
---

---
title: Device orientation events
slug: Web/API/Device_orientation_events
page-type: web-api-overview
browser-compat:
  - api.Window.deviceorientation_event
  - api.Window.devicemotion_event
  - api.Window.deviceorientationabsolute_event
  - api.DeviceOrientationEvent
  - api.DeviceMotionEvent
  - api.DeviceMotionEventAcceleration
  - api.DeviceMotionEventRotationRate
spec-urls: https://w3c.github.io/deviceorientation/
---

{{DefaultAPISidebar("Device Orientation Events")}}{{securecontext_header}}

رویدادهای جهت‌گیری دستگاه، رویدادهایی هستند که به شما امکان می‌دهند [جهت فیزیکی دستگاه را تشخیص دهید](/en-US/docs/Web/API/Device_orientation_events/Detecting_device_orientation#processing_orientation_events) و همچنین [حرکت دستگاه را شناسایی کنید](/en-US/docs/Web/API/Device_orientation_events/Detecting_device_orientation#processing_motion_events).

## مفاهیم و کاربرد

دستگاه‌های همراه معمولاً حسگرهایی مانند ژیروسکوپ، قطبنما و شتاب‌سنج دارند که می‌توانند به برنامه‌های در حال اجرا روی دستگاه امکان تشخیص جهت و حرکت دستگاه را بدهند.

رویدادهای جهت‌گیری دستگاه به شما این امکان را می‌دهند که برنامه‌های وب بنویسید که بتوانند رفتار خود را بر اساس جهت‌گیری دستگاه کاربر تغییر دهند و در هنگام حرکت دستگاه توسط کاربر واکنش نشان دهند.

برخی از کاربردهای معمولی که ممکن است بخواهید از رویدادهای جهت‌گیری دستگاه استفاده کنید عبارت‌اند از:

- در بازی‌های مبتنی بر وب، برای اینکه کاربر بتواند با کج کردن و حرکت دادن دستگاه، حرکت شخصیت‌ها یا اشیاء بازی را کنترل کند.
- در برنامه‌های نقشه، برای تغییر جهت نقشه بر اساس موقعیت دستگاه، یا ارائه مسیریابی گام‌به‌گام که با حرکات کاربر به‌روزرسانی می‌شود.
- برای تشخیص ژست — برای مثال، تشخیص ژست «تکان دادن» و استفاده از آن برای انجام عملی مانند پاک کردن ناحیه ورودی وقتی کاربر دستگاه را تکان می‌دهد.

برخی از عامل‌های کاربر (user agents) پیش از ارائه دسترسی به داده‌های حسگر، اجازه صریح درخواست می‌کنند. در آن محیط‌ها، می‌توان از {{domxref("DeviceMotionEvent.requestPermission_static", "DeviceMotionEvent.requestPermission()")}} و {{domxref("DeviceOrientationEvent.requestPermission_static", "DeviceOrientationEvent.requestPermission()")}} برای درخواست این مجوز از یک {{Glossary("transient activation", "فعال‌سازی گذرا")}} مانند کلیک دکمه استفاده کرد. برای جزئیات بیشتر به [درخواست مجوز](/en-US/docs/Web/API/Device_orientation_events/Detecting_device_orientation#requesting_permission) مراجعه کنید.

> [!NOTE]
> این API به‌طور گسترده‌ای در مرورگرهای موبایل پشتیبانی می‌شود. اگرچه برخی مرورگرهای مخصوص دسکتاپ ممکن است به دلیل تفاوت‌های سخت‌افزاری محدودیت‌هایی داشته باشند، این محدودیت‌ها با توجه به کاربرد اصلی این API در دستگاه‌های مجهز به حسگر، به‌ندرت قابل توجه هستند.

## رابط‌ها

- {{domxref("DeviceMotionEvent")}}
  - : تغییرات شتاب یک دستگاه و همچنین نرخ چرخش آن را نشان می‌دهد.
- {{domxref("DeviceMotionEventAcceleration")}}
  - : میزان شتابی را که دستگاه در طول هر سه محور تجربه می‌کند، نشان می‌دهد.
- {{domxref("DeviceMotionEventRotationRate")}}
  - : نرخی را نشان می‌دهد که دستگاه به دور هر سه محور می‌چرخد.
- {{domxref("DeviceOrientationEvent")}}
  - : تغییرات در جهت‌گیری فیزیکی دستگاه را نشان می‌دهد.

### افزونه‌هایی به دیگر رابط‌ها

- رویداد {{domxref("Window.devicemotion_event", "devicemotion")}}
  - : در بازه‌های زمانی منظم رخ می‌دهد تا میزان نیروی فیزیکی شتابی را که دستگاه در آن زمان دریافت می‌کند و نرخ چرخش دستگاه را نشان دهد.
- رویداد {{domxref("Window.deviceorientation_event", "deviceorientation")}}
  - : زمانی رخ می‌دهد که داده‌های تازه‌ای از دستگاه درباره جهت‌گیری فعلی دستگاه نسبت به چارچوب مختصات زمین در دسترس باشد.
- رویداد {{domxref("Window.deviceorientationabsolute_event", "deviceorientationabsolute")}}
  - : زمانی رخ می‌دهد که جهت‌گیری مطلق دستگاه تغییر کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Device Orientation & Motion](https://web.dev/articles/device-orientation) در web.dev