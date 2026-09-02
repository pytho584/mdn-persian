---
title: "IndexedDB API"
---

---
title: IndexedDB API
slug: Web/API/IndexedDB_API
page-type: web-api-overview
spec-urls: https://w3c.github.io/IndexedDB/
---

{{DefaultAPISidebar("IndexedDB")}} {{AvailableInWorkers}}

ایندکس‌دبی (IndexedDB) یک API سطح پایین برای ذخیره‌سازی سمت کلاینت حجم قابل توجهی از داده‌های ساختیافته، از جمله فایل‌ها و بلاب‌ها (blob) است. این API از ایندکس‌ها برای جستجوی پربازده در این داده‌ها استفاده می‌کند. در حالی که [Web Storage](/en-US/docs/Web/API/Web_Storage_API) برای ذخیره‌سازی مقادیر کمتری از داده مفید است، برای ذخیره‌سازی حجم بیشتری از داده‌های ساختیافته چندان کارآمد نیست. IndexedDB راه‌حلی برای این نیاز ارائه می‌دهد. این صفحه، صفحهٔ اصلی پوشش IndexedDB در MDN است — در اینجا پیوندهایی به مرجع کامل API، راهنماهای استفاده، جزئیات پشتیبانی مرورگرها و توضیحاتی دربارهٔ مفاهیم کلیدی ارائه می‌کنیم.

## مفاهیم و کاربردهای کلیدی

IndexedDB یک سیستم پایگاه‌دادهٔ تراکنشی است، مشابه سیستم مدیریت پایگاه‌دادهٔ رابطه‌ای (RDBMS) مبتنی بر SQL. با این حال، برخلاف RDBMS های مبتنی بر SQL که از جدول‌هایی با ستون‌های ثابت استفاده می‌کنند، IndexedDB یک پایگاه‌دادهٔ شیءگرا مبتنی بر JavaScript است. IndexedDB به شما امکان می‌دهد اشیایی را که با یک **کلید (key)** ایندکس شده‌اند ذخیره و بازیابی کنید؛ هر شیئی که توسط [structured clone algorithm](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) پشتیبانی می‌شود، قابل ذخیره‌سازی است. باید طرح‌وارهٔ پایگاه‌داده را مشخص کنید، اتصالی به پایگاه‌دادهٔ خود باز کنید و سپس داده‌ها را در مجموعه‌ای از **تراکنش‌ها (transactions)** بازیابی و به‌روزرسانی کنید.

- دربارهٔ [IndexedDB key characteristics and basic terminology](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology) بیشتر بخوانید.
- با راهنمای [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB) ما، استفادهٔ ناهمگام از IndexedDB را از اصول اولیه بیاموزید.
- یک مثال کامل و گام‌به‌گام را در راهنمای [checking when a deadline is due](/en-US/docs/Web/API/IndexedDB_API/Checking_when_a_deadline_is_due) ببینید.

> [!NOTE]
> مانند بسیاری از راه‌حل‌های ذخیره‌سازی وب، IndexedDB از [same-origin policy](https://www.w3.org/Security/wiki/Same_Origin_Policy) (خط‌مشی همان مبدأ) پیروی می‌کند. بنابراین در حالی که می‌توانید به داده‌های ذخیره‌شده در یک دامنه دسترسی داشته باشید، نمی‌توانید به داده‌ها در دامنه‌های مختلف دسترسی پیدا کنید.

### همگام و ناهمگام

عملیات انجام‌شده با IndexedDB به‌صورت ناهمگام (asynchronous) اجرا می‌شوند تا برنامه‌ها مسدود نشوند.

### محدودیت‌های ذخیره‌سازی و معیارهای حذف (eviction)

فناوری‌های وب متعددی وجود دارند که داده‌هایی از یک نوع یا نوع دیگر را در سمت کلاینت (یعنی روی دیسک محلی شما) ذخیره می‌کنند. IndexedDB رایج‌ترین موضوع بحث است. فرایندی که مرورگر به‌واسطهٔ آن تعیین می‌کند چه مقدار فضا به ذخیره‌سازی داده‌های وب اختصاص دهد و وقتی آن حد پر شد چه چیزی را حذف کند، ساده نیست و در مرورگرهای مختلف متفاوت است. مقالهٔ [Browser storage quotas and eviction criteria](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) تلاش می‌کند توضیح دهد این فرایند چگونه کار می‌کند، حداقل در مورد Firefox.

## رابط‌ها (Interfaces)

برای دسترسی به یک پایگاه‌داده، متد [`open()`](/en-US/docs/Web/API/IDBFactory/open) را بر روی ویژگی [`indexedDB`](/en-US/docs/Web/API/Window/indexedDB) یک شیء [window](/en-US/docs/Web/API/Window) فراخوانی کنید. این متد یک شیء {{domxref("IDBRequest")}} برمی‌گرداند؛ عملیات ناهمگام با ایجاد رویدادهایی روی اشیاء {{domxref("IDBRequest")}} با برنامهٔ فراخواننده ارتباط برقرار می‌کنند.

### اتصال به یک پایگاه‌داده

- {{domxref("IDBFactory")}}
  - : دسترسی به یک پایگاه‌داده را فراهم می‌کند. یک شیء از این نوع، مقدار ویژگی‌های سراسری {{domxref("Window.indexedDB")}} و {{domxref("WorkerGlobalScope.indexedDB")}} است. بنابراین نقطهٔ ورود به API محسوب می‌شود.
- {{domxref("IDBOpenDBRequest")}}
  - : بیانگر یک درخواست برای باز کردن یک پایگاه‌داده است.
- {{domxref("IDBDatabase")}}
  - : بیانگر یک اتصال به پایگاه‌داده است. این تنها راه دریافت یک تراکنش روی پایگاه‌داده است.

### بازیابی و اصلاح داده‌ها

- {{domxref("IDBTransaction")}}
  - : بیانگر یک تراکنش است. شما روی یک پایگاه‌داده تراکنش ایجاد می‌کنید، محدودهٔ آن (مثلاً اینکه به کدام ذخیره‌گاه‌های شیء می‌خواهید دسترسی داشته باشید) را مشخص می‌کنید، و نوع دسترسی موردنظر (فقط خواندنی یا خواندنی-نوشتنی) را تعیین می‌کنید.
- {{domxref("IDBRequest")}}
  - : رابطی عمومی که درخواست‌های پایگاه‌داده را مدیریت می‌کند و دسترسی به نتایج را فراهم می‌کند.
- {{domxref("IDBObjectStore")}}
  - : بیانگر یک ذخیره‌گاه شیء (object store) است که امکان دسترسی به مجموعه‌ای از داده‌ها در یک پایگاه‌داده IndexedDB را فراهم می‌کند و با استفاده از کلید اصلی جستجو می‌شود.
- {{domxref("IDBIndex")}}
  - : همچنین امکان دسترسی به زیرمجموعه‌ای از داده‌ها در یک پایگاه‌داده IndexedDB را فراهم می‌کند، اما برای بازیابی رکورد(ها) به‌جای کلید اصلی از ایندکس استفاده می‌کند. این کار گاهی سریع‌تر از استفاده از {{domxref("IDBObjectStore")}} است.
- {{domxref("IDBCursor")}}
  - : روی ذخیره‌گاه‌های شیء و ایندکس‌ها پیمایش می‌کند.
- {{domxref("IDBCursorWithValue")}}
  - : روی ذخیره‌گاه‌های شیء و ایندکس‌ها پیمایش می‌کند و مقدار فعلی نشانگر (cursor) را برمی‌گرداند.
- {{domxref("IDBKeyRange")}}
  - : یک بازهٔ کلید (key range) تعریف می‌کند که می‌توان از آن برای بازیابی داده‌ها از یک پایگاه‌داده در بازه‌ای مشخص استفاده کرد.

### رابط‌های رویداد سفارشی

این مشخصات رویدادهایی را با رابط سفارشی زیر ایجاد می‌کند:

- {{domxref("IDBVersionChangeEvent")}}
  - : رابط `IDBVersionChangeEvent` نشان می‌دهد که نسخهٔ پایگاه‌داده در نتیجهٔ اجرای تابع مدیریت رویداد {{domxref("IDBOpenDBRequest.upgradeneeded_event", "IDBOpenDBRequest.onupgradeneeded")}} تغییر کرده است.

## مثال‌ها

- [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([view example live](https://mdn.github.io/dom-examples/to-do-notifications/)): برنامهٔ مرجع برای مثال‌های موجود در مستندات مرجع.

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [Web Storage API](/en-US/docs/Web/API/Web_Storage_API)
- [Window: localStorage property](/en-US/docs/Web/API/Window/localStorage)
- [Window: sessionStorage property](/en-US/docs/Web/API/Window/sessionStorage)
- [StorageEvent](/en-US/docs/Web/API/StorageEvent)