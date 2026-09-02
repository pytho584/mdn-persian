```markdown
---
title: "MessageEvent: MessageEvent() constructor"
short-title: MessageEvent()
slug: Web/API/MessageEvent/MessageEvent
page-type: web-api-constructor
browser-compat: api.MessageEvent.MessageEvent
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

سازندهٔ **`MessageEvent()`** یک شیء جدید از نوع {{domxref("MessageEvent")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new MessageEvent(type)
new MessageEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد را مشخص می‌کند.
    این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را روی `message` قرار می‌دهند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `data` {{optional_inline}}
      - : داده‌ای که می‌خواهید در `MessageEvent` قرار گیرد.
        این می‌تواند از هر نوع داده‌ای باشد و اگر مشخص نشود، پیش‌فرض آن `null` خواهد بود.
    - `origin` {{optional_inline}}
      - : رشته‌ای که مبدأ فرستندهٔ پیام را نشان می‌دهد.
        اگر مشخص نشود، پیش‌فرض آن یک رشتهٔ خالی (`''`) است.
    - `lastEventId` {{optional_inline}}
      - : رشته‌ای که یک شناسهٔ یکتا برای رویداد را نشان می‌دهد.
        اگر مشخص نشود، پیش‌فرض آن یک رشتهٔ خالی (`""`) است.
    - `source` {{optional_inline}}
      - : یک `MessageEventSource` (که می‌تواند یک شیء {{domxref("Window")}}، {{domxref("MessagePort")}} یا {{domxref("ServiceWorker")}} باشد) که فرستندهٔ پیام را نشان می‌دهد.
        اگر تنظیم نشود، پیش‌فرض آن `null` است.
    - `ports` {{optional_inline}}
      - : آرایه‌ای از اشیاء {{domxref("MessagePort")}} که شامل تمام اشیاء {{domxref("MessagePort")}} ارسال‌شده با پیام، به ترتیب، می‌شود.
        اگر مشخص نشود، پیش‌فرض آن یک آرایهٔ خالی (`[]`) است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("MessageEvent")}}.

## مثال‌ها

```js
const myMessage = new MessageEvent("message", {
  data: "hello",
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه این رابط است اما در رابط‌هایی استفاده می‌شود که نیاز به انعطاف‌پذیری بیشتری برای نویسندگان دارند.
```