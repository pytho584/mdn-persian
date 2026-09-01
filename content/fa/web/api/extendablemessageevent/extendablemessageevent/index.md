---
title: "ExtendableMessageEvent: ExtendableMessageEvent() constructor"
short-title: ExtendableMessageEvent()
slug: Web/API/ExtendableMessageEvent/ExtendableMessageEvent
page-type: web-api-constructor
browser-compat: api.ExtendableMessageEvent.ExtendableMessageEvent
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

سازندهٔ **`ExtendableMessageEvent()`** یک شیء جدید {{domxref("ExtendableMessageEvent")}} ایجاد می‌کند.

## Syntax

```js-nolint
new ExtendableMessageEvent(type)
new ExtendableMessageEvent(type, options)
```

### Parameters

- `type`
  - : یک رشته (string) حاوی نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `messageerror` یا `message` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_، می‌تواند دارای ویژگی‌های زیر باشد:
    - `data` {{optional_inline}}
      - : دادهٔ رویداد؛ این می‌تواند هر نوع داده‌ای باشد. مقدار پیش‌فرض `null` است.
    - `origin` {{optional_inline}}
      - : یک رشته که خاستگاه (origin) شیء تنظیمات محیط service worker متناظر را تعریف می‌کند. مقدار پیش‌فرض `""` است.
    - `lastEventId` {{optional_inline}}
      - : یک رشته که آخرین شناسه رویداد (last event ID) منبع رویداد را تعریف می‌کند. مقدار پیش‌فرض `""` است.
    - `source` {{optional_inline}}
      - : {{domxref("Client")}}، {{domxref("ServiceWorker")}} یا {{domxref("MessagePort")}} که پیام را ارسال کرده است. مقدار پیش‌فرض `null` است.
    - `ports` {{optional_inline}}
      - : آرایه‌ای حاوی اشیاء {{domxref("MessagePort")}} متصل به کانال ارسال‌کنندهٔ پیام. مقدار پیش‌فرض یک آرایهٔ خالی است.

### Return value

یک شیء جدید {{domxref("ExtendableMessageEvent")}}.

## Examples

```js
const options = {
  data: "hello message",
  source: MessagePortReference,
  ports: MessagePortListReference,
};

const myEME = new ExtendableMessageEvent("message", init);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه Service Workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [پیام‌رسانی کانال (Channel Messaging)](/en-US/docs/Web/API/Channel_Messaging_API)