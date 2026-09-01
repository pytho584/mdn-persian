---
title: DedicatedWorkerGlobalScope
slug: Web/API/DedicatedWorkerGlobalScope
page-type: web-api-interface
browser-compat: api.DedicatedWorkerGlobalScope
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

شیء **`DedicatedWorkerGlobalScope`** (حوزهٔ سراسری {{domxref("Worker")}}) از طریق کلیدواژهٔ {{domxref("WorkerGlobalScope.self","self")}} در دسترس است. برخی توابع سراسری، اشیاء فضاهای نام، و سازنده‌های اضافی که معمولاً با حوزهٔ سراسری worker مرتبط نیستند، اما روی آن در دسترس هستند، در [مرجع جاوااسکریپت](/en-US/docs/Web/JavaScript/Reference) فهرست شده‌اند. همچنین ببینید: [توابع در دسترس برای workerها](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers).

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط ویژگی‌ها را از رابط {{domxref("WorkerGlobalScope")}} و والد آن {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("DedicatedWorkerGlobalScope.name")}} {{ReadOnlyInline}}
  - : نامی که به {{domxref("Worker")}} هنگام ایجاد با سازندهٔ {{domxref("Worker.Worker", "Worker()")}} (به‌صورت اختیاری) داده شده است. این مقدار عمدتاً برای اشکال‌زدایی مفید است.

## متدهای نمونه

_این رابط متدها را از رابط {{domxref("WorkerGlobalScope")}} و والد آن {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("DedicatedWorkerGlobalScope.close()")}}
  - : هر وظیفه‌ای که در صف حلقهٔ رویداد `WorkerGlobalScope` قرار دارد را کنار می‌گذارد و عملاً این حوزهٔ خاص را می‌بندد.
- {{domxref("DedicatedWorkerGlobalScope.postMessage()")}}
  - : یک پیام — که می‌تواند شامل `any` (هر) شیء جاوااسکریپتی باشد — به سند والد که ابتدا worker را ایجاد کرد ارسال می‌کند.
- {{domxref("DedicatedWorkerGlobalScope.cancelAnimationFrame()")}}
  - : یک درخواست فریم انیمیشن را که قبلاً از طریق فراخوانی {{domxref("DedicatedWorkerGlobalScope.requestAnimationFrame()", "requestAnimationFrame()")}} زمان‌بندی شده بود، لغو می‌کند.
- {{domxref("DedicatedWorkerGlobalScope.requestAnimationFrame()")}}
  - : یک درخواست فریم انیمیشن انجام می‌دهد و قبل از بازکشی (repaint) بعدی، یک تابع callback که توسط کاربر ارائه شده را فراخوانی می‌کند.

## رویدادها

برای گوش‌دادن به این رویداد، از {{domxref("EventTarget/addEventListener()", "addEventListener()")}} استفاده کنید یا یک شنوندهٔ رویداد را به ویژگی `oneventname` این رابط نسبت دهید.

- {{domxref("DedicatedWorkerGlobalScope/message_event", "message")}}
  - : زمانی که worker پیامی را از والد خود دریافت می‌کند، فعال می‌شود.
- {{domxref("DedicatedWorkerGlobalScope/messageerror_event", "messageerror")}}
  - : زمانی که یک worker پیامی را دریافت می‌کند که نمی‌توان آن را از حالت سریال‌سازی خارج کرد (deserialize)، فعال می‌شود.
- {{domxref("DedicatedWorkerGlobalScope/rtctransform_event", "rtctransform")}}
  - : زمانی که یک فریم ویدیویی یا صوتی رمزگذاری‌شده برای پردازش توسط {{domxref("WebRTC API/Using Encoded Transforms", "WebRTC Encoded Transform", "", "nocode")}} در صف قرار می‌گیرد، فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Worker")}}
- {{domxref("WorkerGlobalScope")}}
- [استفاده از web workerها](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)
- [توابع در دسترس برای workerها](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers)