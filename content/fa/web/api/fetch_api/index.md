---
title: "Fetch API"
slug: Web/API/Fetch_API
page-type: web-api-overview
browser-compat:
  - api.fetch
  - api.Window.fetchLater
---

{{DefaultAPISidebar("Fetch API")}}

Fetch API واسطه‌ای برای دریافت منابع (از جمله از طریق شبکه) فراهم می‌کند. این API جایگزینی قدرتمندتر و انعطاف‌پذیرتر برای {{DOMxRef("XMLHttpRequest")}} است.

## مفاهیم و کاربرد

Fetch API از اشیاء {{DOMxRef("Request")}} و {{DOMxRef("Response")}} (و سایر موارد مرتبط با درخواست‌های شبکه)، و همچنین مفاهیم مرتبط مانند CORS و معنا‌شناسی هدر HTTP Origin استفاده می‌کند.

برای ارسال درخواست و دریافت یک منبع، از متد {{domxref("Window/fetch", "fetch()")}} استفاده کنید. این یک متد سراسری در هر دو بافتار {{DOMxRef("Window")}} و {{DOMxRef("WorkerGlobalScope", "Worker")}} است. این موضوع باعث می‌شود که تقریباً در هر بافتاری که بخواهید منابعی را دریافت کنید، در دسترس باشد.

متد `fetch()` یک آرگومان اجباری می‌گیرد: مسیر منبعی که می‌خواهید دریافت کنید. این متد یک {{JSxRef("Promise")}} برمی‌گرداند که با {{DOMxRef("Response")}} به آن درخواست حل می‌شود — به محض اینکه سرور با هدرها پاسخ دهد — **حتی اگر پاسخ سرور یک وضعیت خطای HTTP باشد**. همچنین می‌توانید به‌صورت اختیاری یک شیء گزینه `init` را به‌عنوان آرگومان دوم پاس دهید (به {{DOMxRef("Request")}} مراجعه کنید).

پس از دریافت {{DOMxRef("Response")}}، روش‌های متعددی برای تعیین محتوای بدنه و نحوه مدیریت آن در دسترس هستند.

می‌توانید مستقیماً با استفاده از سازنده‌های {{DOMxRef("Request.Request", "Request()")}} و {{DOMxRef("Response.Response", "Response()")}} یک درخواست و پاسخ ایجاد کنید، اما انجام مستقیم این کار رایج نیست. در عوض، این اشیاء معمولاً به‌عنوان نتایج سایر اقدامات API ایجاد می‌شوند (برای مثال، {{DOMxRef("FetchEvent.respondWith()")}} در service workerها).

برای آشنایی بیشتر با امکانات Fetch API، به [استفاده از Fetch](/en-US/docs/Web/API/Fetch_API/Using_Fetch) مراجعه کنید.

### دریافت معوق (Deferred Fetch)

API مربوط به {{domxref("Window/fetchLater", "fetchLater()")}} به توسعه‌دهنده امکان می‌دهد یک _دریافت معوق_ درخواست کند که می‌تواند پس از مدت زمان مشخصی، یا زمانی که صفحه بسته می‌شود یا از آن خارج می‌شوید، ارسال شود. به [استفاده از دریافت معوق](/en-US/docs/Web/API/Fetch_API/Using_Deferred_Fetch) مراجعه کنید.

## رابط‌ها (Interfaces)

- {{domxref("Window.fetch()")}} و {{domxref("WorkerGlobalScope.fetch()")}}
  - : متد `fetch()` که برای دریافت یک منبع استفاده می‌شود.
- {{domxref("Window.fetchLater()")}}
  - : برای انجام یک درخواست دریافت معوق استفاده می‌شود.
- {{domxref("DeferredRequestInit")}}
  - : مجموعه گزینه‌هایی را نشان می‌دهد که می‌توانند برای پیکربندی یک درخواست دریافت معوق استفاده شوند.
- {{domxref("FetchLaterResult")}}
  - : نتیجه درخواست یک دریافت معوق را نشان می‌دهد.
- {{DOMxRef("Headers")}}
  - : هدرهای پاسخ/درخواست را نشان می‌دهد و به شما امکان می‌دهد آن‌ها را جستجو کرده و بسته به نتایج، اقدامات متفاوتی انجام دهید.
- {{DOMxRef("Request")}}
  - : یک درخواست منبع را نشان می‌دهد.
- {{DOMxRef("Response")}}
  - : پاسخ به یک درخواست را نشان می‌دهد.

## هدرهای HTTP

- {{HTTPHeader("Permissions-Policy/deferred-fetch", "deferred-fetch")}}
  - : [سهمیه سطح بالا](/en-US/docs/Web/API/Fetch_API/Using_Deferred_Fetch#quotas) برای API مربوط به `fetchLater()` را کنترل می‌کند.
- {{HTTPHeader("Permissions-Policy/deferred-fetch-minimal", "deferred-fetch-minimal")}}
  - : [سهمیه مشترک زیر‌فریم متقاطع‌المنشأ](/en-US/docs/Web/API/Fetch_API/Using_Deferred_Fetch#quotas) برای API مربوط به `fetchLater()` را کنترل می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Fetch](/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
- [دسترسی به شبکه محلی](/en-US/docs/Web/Security/Defenses/Local_network_access)