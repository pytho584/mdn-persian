---
title: "Event: Event() constructor"
short-title: Event()
slug: Web/API/Event/Event
page-type: web-api-constructor
browser-compat: api.Event.Event
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

سازندهٔ **`Event()`** یک شیء جدید {{domxref("Event")}} می‌سازد. به رخدادی که به این شکل ساخته می‌شود، _رخداد مصنوعی_ گفته می‌شود، در مقابل رخدادی که توسط مرورگر شلیک می‌شود، و می‌تواند توسط یک اسکریپت [توزیع](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) شود.

## Syntax

```js-nolint
new Event(type)
new Event(type, options)
```

### مقادیر

- `type`
  - : یک رشته (string) با نام رخداد.
- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `bubbles` {{optional_inline}}
      - : یک مقدار بولی (boolean) که نشان می‌دهد آیا رخداد حباب می‌زند (bubbles) یا خیر. پیش‌فرض
        `false` است.
    - `cancelable` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا رخداد قابل لغو شدن است یا خیر. پیش‌فرض
        `false` است.
    - `composed` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا رخداد شنوندگان (listeners) خارج از ریشه سایه (shadow root) را فعال می‌کند یا خیر (برای جزئیات بیشتر به {{domxref("Event.composed")}} مراجعه کنید). پیش‌فرض
        `false` است.

### مقدار بازگشتی

یک شیء جدید {{domxref("Event")}}.

## مثال

```js
// create a look event that bubbles up and cannot be canceled

const evt = new Event("look", { bubbles: true, cancelable: false });
document.dispatchEvent(evt);

// event can be dispatched from any element, not only the document
myDiv.dispatchEvent(evt);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Event")}}
- {{domxref("EventTarget.dispatchEvent()")}}
- [Creating and dispatching events](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events)