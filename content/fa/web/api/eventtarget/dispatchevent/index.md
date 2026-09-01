---
title: "EventTarget: dispatchEvent() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/dispatchEvent"
---

---
title: "EventTarget: dispatchEvent() method"
short-title: dispatchEvent()
slug: Web/API/EventTarget/dispatchEvent
page-type: web-api-instance-method
browser-compat: api.EventTarget.dispatchEvent
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

متد **`dispatchEvent()`** در {{domxref("EventTarget")}} یک {{domxref("Event")}} را به شیء می‌فرستد و به‌صورت همزمان (synchronously) شنونده‌های رویداد مربوطه را به ترتیب مناسب فراخوانی می‌کند. قواعد عادی پردازش رویداد (شامل فازهای capturing و اختیاری bubbling) برای رویدادهایی که به‌صورت دستی با `dispatchEvent()` ارسال می‌شوند نیز اعمال می‌شود.

فراخوانی `dispatchEvent()` آخرین گام برای _پدید آوردن یک رویداد_ است. رویداد باید پیش از این با استفاده از سازنده {{domxref("Event/Event", "Event()")}} ساخته و مقداردهی شده باشد.

> [!NOTE]
> هنگام فراخوانی این متد، ویژگی {{domxref("Event.target")}} به `EventTarget` فعلی مقداردهی می‌شود.

برخلاف رویدادهای «بومی» که مرورگر با قرار دادن یک کار (task) در [حلقه رویداد](/en-US/docs/Web/JavaScript/Reference/Execution_model#job_queue_and_event_loop) آن‌ها را اجرا می‌کند، `dispatchEvent()` همهٔ مدیریت‌کننده‌های رویدادِ مرتبط را به‌صورت همزمان و پیش از بازگشت فراخوانی می‌کند. ویژگی فقط‌خواندنی [`isTrusted`](/en-US/docs/Web/API/Event/isTrusted) برای رویدادهای بومی `true` و برای رویدادهایی که با `dispatchEvent()` ارسال می‌شوند `false` است.

## Syntax

```js-nolint
dispatchEvent(event)
```

### Parameters

- `event`
  - : شیء {{domxref("Event")}} که قرار است ارسال شود. ویژگی {{domxref("Event.target")}} آن روی {{domxref("EventTarget")}} فعلی تنظیم خواهد شد.

### Return value

اگر `event` قابل لغو (cancelable) باشد و حداقل یکی از مدیریت‌کننده‌های رویداد که `event` را دریافت کرده‌اند، {{domxref("Event.preventDefault()")}} را فراخوانده باشد، مقدار `false` برمی‌گردد. در غیر این صورت `true` برمی‌گردد.

### Exceptions

- `InvalidStateError` {{domxref("DomException")}}
  - : اگر نوع رویداد در هنگام مقداردهی اولیه رویداد مشخص نشده باشد، این خطا پرتاب می‌شود.

> [!WARNING]
> استثناهایی که توسط مدیریت‌کننده‌های رویداد پرتاب می‌شوند به‌عنوان استثناهای uncaught گزارش می‌شوند. مدیریت‌کننده‌های رویداد روی یک پشته فراخوانی تو در تو اجرا می‌شوند؛ آن‌ها تا پایان کار، فراخواننده را مسدود می‌کنند، اما استثناها به فراخواننده منتقل نمی‌شوند.

## Example

برای مشاهده مثال، [ساخت و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) را ببینید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [مرجع شیء Event](/en-US/docs/Web/API/Event)