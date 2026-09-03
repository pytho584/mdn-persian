---
title: "Navigator: scheduling property"
short-title: scheduling
slug: Web/API/Navigator/scheduling
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.scheduling
---

{{SeeCompatTable}}{{APIRef("Prioritized Task Scheduling API")}}

خاصیت فقط-خواندنی **`scheduling`** از رابط {{domxref("Navigator")}} یک شیء {{domxref("Scheduling")}} برای سند جاری برمی‌گرداند که متدها و ویژگی‌هایی برای کنترل زمان‌بندی وظایف ارائه می‌دهد.

> [!WARNING]
> رابط {{domxref("Scheduling")}} (که شامل متد {{domxref("Scheduling.isInputPending()", "isInputPending()")}} است) توسط رابط {{domxref("Scheduler")}} جایگزین شده است، ویژگی‌های آن برای پرداختن به زمان‌بندی وظایف بهتر طراحی شده‌اند. برای جزئیات بیشتر به [از `isInputPending()` استفاده نکنید](https://web.dev/articles/optimize-long-tasks#isinputpending) مراجعه کنید.

## مقدار

یک شیء {{domxref("Scheduling")}}.

## مثال

برای یک مثال کامل، صفحه {{domxref("Scheduling.isInputPending()")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("Scheduler")}}
- {{domxref("Prioritized_task_scheduling_api", "API زمان‌بندی وظایف اولویت‌بندی شده", "", "nocode")}}
- [رویدادهای ورودی سریع‌تر با اولین مشارکت API مرورگر فیسبوک](https://engineering.fb.com/2019/04/22/developer-tools/isinputpending-api/) در engineering.fb.com (2019)
- [زمان‌بندی بهتر JS با `isInputPending()`](https://developer.chrome.com/docs/capabilities/web-apis/isinputpending) در developer.chrome.com (2020)
- [بهینه‌سازی وظایف طولانی](https://web.dev/articles/optimize-long-tasks) در web.dev (2022)