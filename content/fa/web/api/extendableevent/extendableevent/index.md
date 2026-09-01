---
title: "ExtendableEvent: ExtendableEvent() constructor"
short-title: ExtendableEvent()
slug: Web/API/ExtendableEvent/ExtendableEvent
page-type: web-api-constructor
browser-compat: api.ExtendableEvent.ExtendableEvent
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

سازندهٔ **`ExtendableEvent()`** یک شیء جدید از نوع {{domxref("ExtendableEvent")}} می‌سازد.

## Syntax

```js-nolint
new ExtendableEvent(type)
new ExtendableEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این نام به حروف بزرگ و کوچک حساس است.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند هر تنظیمات سفارشی‌ای را که می‌خواهید روی شیء رویداد اعمال کنید، شامل شود.
    در حال حاضر هیچ گزینهٔ اجباری‌ای وجود ندارد،
    اما این امکان برای سازگاری با رویدادهای مشتق‌شدهٔ مختلف در آینده در نظر گرفته شده است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("ExtendableEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workerها](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایهٔ Service workerها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از web workerها](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)