---
title: "PushEvent: PushEvent() constructor"
short-title: PushEvent()
slug: Web/API/PushEvent/PushEvent
page-type: web-api-constructor
browser-compat: api.PushEvent.PushEvent
---

{{APIRef("Push API")}}{{SecureContext_Header}}{{AvailableInWorkers("service")}}

سازندهٔ **`PushEvent()`** یک شیء جدید {{domxref("PushEvent")}} می‌سازد. توجه داشته باشید که این سازنده فقط در زمینهٔ سرویس‌ورکر (Service Worker) در دسترس است.

## سینتکس

```js-nolint
new PushEvent(type)
new PushEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای (string) است که نام رویداد را مشخص می‌کند.
    این مقدار به بزرگی و کوچکی حروف حساس است (case-sensitive) و مرورگرها آن را روی `push` یا `pushsubscriptionchange` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء است که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `data`
      - : داده‌ای است که می‌خواهید `PushEvent` شامل آن باشد (در صورت وجود).
        هنگام فراخواندن سازنده، ویژگی {{domxref("PushEvent.data")}} شیء حاصل، روی یک شیء جدید {{domxref("PushMessageData")}} حاوی این بایت‌ها تنظیم می‌شود.

### مقدار بازگشتی

یک شیء جدید {{domxref("PushEvent")}}.

## مثال‌ها

```js
const dataInit = {
  data: "Some sample text",
};

const myPushEvent = new PushEvent("push", dataInit);

myPushEvent.data.text(); // should return 'Some sample text'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Push API](/en-US/docs/Web/API/Push_API)
- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)
