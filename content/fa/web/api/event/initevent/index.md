---
title: "Event: initEvent() method"
short-title: initEvent()
slug: Web/API/Event/initEvent
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Event.initEvent
---

{{APIRef("DOM")}}{{deprecated_header}}{{AvailableInWorkers}}

متد **`Event.initEvent()`** برای مقداردهی اولیه به رویدادی استفاده می‌شود که با استفاده از {{domxref("Document.createEvent()")}} ساخته شده است.

رویدادهایی که به این روش مقداردهی می‌شوند باید با متد {{domxref("Document.createEvent()")}} ایجاد شده باشند. این متد باید قبل از ارسال رویداد، برای تنظیم آن فراخوانی شود و ارسال با استفاده از {{domxref("EventTarget.dispatchEvent()")}} انجام می‌شود. پس از ارسال، این متد دیگر هیچ کاری انجام نمی‌دهد.

> [!NOTE]
> _دیگر از این متد استفاده نکنید، زیرا منسوخ شده است._
> در عوض از سازنده‌های اختصاصی رویداد، مانند {{domxref("Event.Event", "Event()")}} استفاده کنید. بخش [ایجاد و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) اطلاعات بیشتری درباره نحوه استفاده از این سازنده‌ها ارائه می‌دهد.

## Syntax

```js-nolint
initEvent(type, bubbles, cancelable)
```

### پارامترها

- `type`
  - : یک رشته که نوع رویداد را مشخص می‌کند.
- `bubbles`
  - : یک مقدار بولی که تعیین می‌کند آیا رویداد باید در زنجیره رویداد به سمت بالا منتشر شود یا نه. پس از تنظیم، ویژگی فقط‌خواندنی {{ domxref("Event.bubbles") }} مقدار آن را نشان می‌دهد.
- `cancelable`
  - : یک مقدار بولی که تعیین می‌کند آیا رویداد قابل لغو است یا نه. پس از تنظیم، ویژگی فقط‌خواندنی {{ domxref("Event.cancelable") }} مقدار آن را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام.

## مثال

```js
// Create the event.
const event = document.createEvent("Event");

// Create a click event that bubbles up and
// cannot be canceled
event.initEvent("click", true, false);

// Listen for the event.
elem.addEventListener("click", (e) => {
  // e.target matches elem
});

elem.dispatchEvent(event);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سازنده‌ای که باید به جای این متد منسوخ استفاده شود:
  {{domxref("Event.Event", "Event()")}}. برای ساخت اینترفیس‌های رویداد خاص‌تر از `Event`، از سازنده تعریف‌شده برای اینترفیس رویداد موردنظر استفاده کنید.