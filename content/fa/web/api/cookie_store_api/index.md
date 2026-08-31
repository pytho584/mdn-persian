---
title: "Cookie Store API"
---

---
title: Cookie Store API
slug: Web/API/Cookie_Store_API
page-type: web-api-overview
browser-compat:
  - api.CookieStore
  - api.CookieStoreManager
spec-urls: https://cookiestore.spec.whatwg.org/
---

{{securecontext_header}}{{DefaultAPISidebar("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

**Cookie Store API** یک API ناهمگام برای مدیریت کوکی‌ها است که در پنجره‌ها و همچنین [سرویس‌ورکرها](/en-US/docs/Web/API/Service_Worker_API) در دسترس است.

## مفاهیم و کاربرد

روش اصلی دریافت و تنظیم کوکی‌ها شامل کار با {{domxref("document.cookie")}} برای دریافت و تنظیم اطلاعات کوکی به‌صورت یک رشته از جفت‌های کلید/مقدار است. این روش علاوه بر اینکه دست‌وپاگیر و مستعد خطاست، در بستر توسعه وب مدرن نیز مشکلات متعددی به همراه دارد.

رابط `document.cookie` {{Glossary("synchronous")}} (همگام)، تک‌نخی، و مسدودکننده است. هنگام نوشتن یک کوکی، باید منتظر بمانید تا مرورگر رشته همه کوکی‌ها را به‌روزرسانی کند. علاوه بر این، وابستگی به {{domxref("document")}} به این معناست که سرویس‌ورکرها نمی‌توانند به کوکی‌ها دسترسی داشته باشند، زیرا آن‌ها به شیء `document` دسترسی ندارند.

_Cookie Store API_ روشی به‌روز برای مدیریت کوکی‌ها فراهم می‌کند. این API {{Glossary("asynchronous")}} (ناهمگام) و مبتنی بر Promise است؛ بنابراین حلقه رویداد (event loop) را مسدود نمی‌کند. به {{domxref("Document")}} وابسته نیست و در نتیجه در دسترس سرویس‌ورکرها قرار دارد. روش‌های دریافت و تنظیم کوکی‌ها همچنین از طریق پیام‌های خطا، بازخورد بیشتری ارائه می‌دهند. این بدان معناست که توسعه‌دهندگان وب مجبور نیستند برای اطمینان از موفقیت‌آمیز بودن تنظیم، بلافاصله کوکی را دوباره بخوانند.

## رابط‌ها

- {{domxref("CookieStore")}} {{Experimental_Inline}}
  - : رابط `CookieStore` امکان دریافت و تنظیم کوکی‌ها را فراهم می‌کند.
- {{domxref("CookieStoreManager")}} {{Experimental_Inline}}
  - : رابط `CookieStoreManager` یک ثبت‌نام (registration) سرویس‌ورکر فراهم می‌کند تا سرویس‌ورکرها بتوانند در رویدادهای تغییر کوکی مشترک شوند.
- {{domxref("CookieChangeEvent")}} {{Experimental_Inline}}
  - : یک `CookieChangeEvent` به نام `change` زمانی که هر تغییری در کوکی‌های قابل مشاهده توسط اسکریپت رخ دهد، در بافت‌های {{domxref("Window")}} علیه اشیاء `CookieStore` گسیل می‌شود.
- {{domxref("ExtendableCookieChangeEvent")}}
  - : زمانی که هر تغییر قابل مشاهده توسط اسکریپت در کوکی‌ها رخ دهد که با فهرست اشتراک تغییر کوکی سرویس‌ورکر مطابقت داشته باشد، یک `ExtendableCookieChangeEvent` به نام `cookiechange` در بافت‌های {{domxref("ServiceWorkerGlobalScope")}} گسیل می‌شود.

### توسعه‌هایی برای سایر رابط‌ها

- {{domxref("ServiceWorkerGlobalScope.cookieStore")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک ارجاع به شیء {{domxref("CookieStore")}} مرتبط با سرویس‌ورکر برمی‌گرداند.
- {{domxref("ServiceWorkerRegistration.cookies")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک ارجاع به رابط {{domxref("CookieStoreManager")}} برمی‌گرداند که به یک وب‌اپلیکیشن امکان می‌دهد در رویدادهای تغییر کوکی مشترک شود یا اشتراک خود را لغو کند.
- {{domxref("Window.cookieStore")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک ارجاع به شیء {{domxref("CookieStore")}} برای بافت سند جاری برمی‌گرداند.
- {{domxref("ServiceWorkerGlobalScope/cookiechange_event", "cookiechange")}} event {{Experimental_Inline}}
  - : وقتی شلیک می‌شود که هر تغییری در کوکی‌ها رخ داده باشد که با فهرست اشتراک تغییر کوکی سرویس‌ورکر مطابقت داشته باشد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)