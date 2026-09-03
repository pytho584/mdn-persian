---
title: "Performance"
---

---
title: Performance
slug: Web/API/Performance
page-type: web-api-interface
browser-compat: api.Performance
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

رابطِ **`Performance`** دسترسی به اطلاعات مرتبط با عملکردِ صفحهٔ کنونی را فراهم میکند.

ورودیهای عملکرد (Performance entries) مخصوص هر بستر اجرایی (execution context) هستند. شما میتوانید اطلاعات عملکردِ کدی که در یک پنجره اجرا میشود را از طریق {{domxref("Window.performance")}} و اطلاعات عملکردِ کدی که در یک worker اجرا میشود را از طریق {{domxref("WorkerGlobalScope.performance")}} دریافت کنید.

{{InheritanceDiagram}}

## ویژگیهای نمونه

_رابطِ `Performance` هیچ ویژگیای را به ارث نمیبرد._

- {{domxref("Performance.eventCounts")}} {{ReadOnlyInline}}
  - : یک نقشهٔ {{domxref("EventCounts")}} که شامل تعداد رویدادهای ارسالشده به ازای هر نوع رویداد است.
- {{domxref("Performance.interactionCount")}} {{ReadOnlyInline}}
  - : تعداد تعاملات کاربرِ واقعی که در صفحه رخ داده است؛ این مقدار هنگام محاسبهٔ {{Glossary("Interaction_to_next_paint", "Interaction to Next Paint (INP)")}} مفید است.
- {{domxref("Performance.navigation")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : یک شیء قدیمی {{domxref("PerformanceNavigation")}} که زمینهٔ مفیدی را دربارهٔ عملیات موجود در زمانهای فهرستشده در `timing` فراهم میکند؛ از جمله اینکه آیا صفحه بارگذاری شده یا بازخوانی (refresh) شده است، چند بار تغییر مسیر رخ داده است و مواردی از این دست.
- {{domxref("Performance.timing")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : یک شیء قدیمی {{domxref("PerformanceTiming")}} که حاوی اطلاعات عملکرد مرتبط با تأخیر است.
- {{domxref("Performance.memory")}} {{ReadOnlyInline}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : یک افزونهٔ _غیراستاندارد_ که در Chrome اضافه شده است؛ این ویژگی شیئی با اطلاعات پایهٔ مصرف حافظه فراهم میکند. _شما **نباید** از این API غیراستاندارد استفاده کنید._
- {{domxref("Performance.timeOrigin")}} {{ReadOnlyInline}}
  - : زمان شروعِ اندازهگیری عملکرد را به صورت یک برچسب زمانی با وضوح بالا (high resolution timestamp) برمیگرداند.

## روشهای نمونه

_رابطِ `Performance` هیچ روشی را به ارث نمیبرد._

- {{domxref("Performance.clearMarks()")}}
  - : _mark_ دادهشده را از بافر ورودیهای عملکرد مرورگر حذف میکند.
- {{domxref("Performance.clearMeasures()")}}
  - : _measure_ دادهشده را از بافر ورودیهای عملکرد مرورگر حذف میکند.
- {{domxref("Performance.clearResourceTimings()")}}
  - : همهٔ [ورودیهای عملکرد](/en-US/docs/Web/API/PerformanceEntry) با {{domxref("PerformanceEntry.entryType","entryType")}} برابر با `"resource"` را از بافر دادههای عملکرد مرورگر حذف میکند.
- {{domxref("Performance.getEntries()")}}
  - : فهرستی از اشیاء {{domxref("PerformanceEntry")}} را بر اساس _فیلتر_ دادهشده برمیگرداند.
- {{domxref("Performance.getEntriesByName()")}}
  - : فهرستی از اشیاء {{domxref("PerformanceEntry")}} را بر اساس _نام_ و _نوع ورودی_ دادهشده برمیگرداند.
- {{domxref("Performance.getEntriesByType()")}}
  - : فهرستی از اشیاء {{domxref("PerformanceEntry")}} از _نوع ورودی_ دادهشده را برمیگرداند.
- {{domxref("Performance.mark()")}}
  - : یک {{domxref("DOMHighResTimeStamp","timestamp")}} را با نام دادهشده در _بافر ورودیهای عملکرد_ مرورگر ایجاد میکند.
- {{domxref("Performance.measure()")}}
  - : یک {{domxref("DOMHighResTimeStamp","timestamp")}} نامدار را در بافر ورودیهای عملکرد مرورگر بین دو mark مشخصشده (به ترتیب با نامهای _start mark_ و _end mark_) ایجاد میکند.
- {{domxref("Performance.measureUserAgentSpecificMemory()")}} {{Experimental_Inline}}
  - : میزان مصرف حافظهٔ یک برنامهٔ وب را شامل همهٔ iframeها و workerهای آن تخمین میزند.
- {{domxref("Performance.now()")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمیگرداند که تعداد میلیثانیههای سپریشده از یک لحظهٔ مرجع را نشان میدهد.
- {{domxref("Performance.setResourceTimingBufferSize()")}}
  - : اندازهٔ بافر زمانبندی منابع (resource timing buffer) مرورگر را به تعداد مشخصشده از اشیاء {{domxref("PerformanceEntry")}} با {{domxref("PerformanceEntry.entryType","نوع")}} `"resource"` تنظیم میکند.
- {{domxref("Performance.toJSON()")}}
  - : یک نمایش JSON از شیءِ `Performance` برمیگرداند.

## رویدادها

به این رویدادها با استفاده از `addEventListener()` یا با اختصاص دادن یک شنوندهٔ رویداد به ویژگیِ `oneventname` این رابط گوش دهید.

- {{DOMxRef("Performance.resourcetimingbufferfull_event", "resourcetimingbufferfull")}}
  - : زمانی که [بافر زمانبندی منابع](/en-US/docs/Web/API/Performance/setResourceTimingBufferSize) مرورگر پر میشود، این رویداد رخ میدهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}