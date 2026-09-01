---
title: "Document: createEvent() method"
short-title: createEvent()
slug: Web/API/Document/createEvent
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Document.createEvent
---

{{APIRef("DOM")}}{{deprecated_header}}

> [!WARNING]
> بسیاری از روشهایی که با `createEvent` به کار میروند، مانند `initCustomEvent`، منسوخ شدهاند.
> به جای آن از [سازندههای رویداد](/en-US/docs/Web/API/CustomEvent) استفاده کنید.

یک [رویداد](/en-US/docs/Web/API/Event) از نوع مشخصشده ایجاد میکند. شیء بازگشتیدادهشده ابتدا باید مقداردهی اولیه شود و سپس میتوان آن را به {{domxref("EventTarget.dispatchEvent")}} ارسال کرد.

## نحو

```js-nolint
createEvent(type)
```

### پارامترها

- `type`
  - : رشتهای که نوع رویداد مورد نظر برای ایجاد را نشان میدهد. انواع رویداد ممکن شامل `"UIEvents"`، `"MouseEvents"`، `"MutationEvents"` و `"HTMLEvents"` است. برای جزئیات بیشتر، بخش [یادداشتها](#notes) را ببینید.

### مقدار بازگشتی

یک شیء [Event](/en-US/docs/Web/API/Event).

## مثالها

```js
// Create the event.
const event = document.createEvent("Event");

// Define that the event name is 'build'.
event.initEvent("build", true, true);

// Listen for the event.
elem.addEventListener("build", (e) => {
  // e.target matches elem
});

// Target can be any Element or other EventTarget.
elem.dispatchEvent(event);
```

## یادداشتها

رشتههای نوع رویداد مناسب برای ارسال به `createEvent()` در [استاندارد DOM — جدول مرحله ۲ را ببینید](https://dom.spec.whatwg.org/#dom-document-createevent) فهرست شدهاند. توجه داشته باشید که اکنون بیشتر اشیاء رویداد سازندههای مخصوص به خود را دارند که روش مدرن و توصیهشده برای ایجاد نمونههای شیء رویداد هستند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ایجاد و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events)