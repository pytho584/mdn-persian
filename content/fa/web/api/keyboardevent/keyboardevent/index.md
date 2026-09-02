---
title: "KeyboardEvent: KeyboardEvent() constructor"
short-title: KeyboardEvent()
slug: Web/API/KeyboardEvent/KeyboardEvent
page-type: web-api-constructor
browser-compat: api.KeyboardEvent.KeyboardEvent
---

{{APIRef("UI Events")}}

سازنده **`KeyboardEvent()`** یک شیء جدید از نوع {{domxref("KeyboardEvent")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new KeyboardEvent(type)
new KeyboardEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته (string) با نام رویداد.
    این نام به حروف بزرگ و کوچک حساس است و مرورگرها آن را روی `keydown`، `keyup` یا `keypress` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("UIEvent/UIEvent", "UIEvent()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `key` {{optional_inline}}
      - : یک رشته، پیش‌فرض `""`، که مقدار {{domxref("KeyboardEvent.key")}} را تنظیم می‌کند.
    - `code` {{optional_inline}}
      - : یک رشته، پیش‌فرض `""`، که مقدار {{domxref("KeyboardEvent.code")}} را تنظیم می‌کند.
    - `location` {{optional_inline}}
      - : یک عدد، پیش‌فرض `0`، که مقدار {{domxref("KeyboardEvent.location")}} را تنظیم می‌کند.
    - `repeat` {{optional_inline}}
      - : یک مقدار بولی (boolean)، پیش‌فرض `false`، که مقدار {{domxref("KeyboardEvent.repeat")}} را تنظیم می‌کند.
    - `isComposing` {{optional_inline}}
      - : یک مقدار بولی، پیش‌فرض `false`، که مقدار {{domxref("KeyboardEvent.isComposing")}} را تنظیم می‌کند.
    - `charCode` {{optional_inline}} {{deprecated_inline}}
      - : یک عدد، پیش‌فرض `0`، که مقدار ویژگی منسوخ‌شده {{domxref("KeyboardEvent.charCode")}} را تنظیم می‌کند.
    - `keyCode` {{optional_inline}} {{deprecated_inline}}
      - : یک عدد، پیش‌فرض `0`، که مقدار ویژگی منسوخ‌شده {{domxref("KeyboardEvent.keyCode")}} را تنظیم می‌کند.
    - `which` {{optional_inline}} {{deprecated_inline}}
      - : یک عدد، پیش‌فرض `0`، که مقدار ویژگی منسوخ‌شده {{domxref("UIEvent.which")}} را تنظیم می‌کند.
    - `ctrlKey` {{optional_inline}}
      - : یک مقدار بولی، پیش‌فرض `false`، که مقدار {{domxref("KeyboardEvent.ctrlKey")}} را تنظیم می‌کند.
    - `shiftKey` {{optional_inline}}
      - : یک مقدار بولی، پیش‌فرض `false`، که مقدار {{domxref("KeyboardEvent.shiftKey")}} را تنظیم می‌کند.
    - `altKey` {{optional_inline}}
      - : یک مقدار بولی، پیش‌فرض `false`، که مقدار {{domxref("KeyboardEvent.altKey")}} را تنظیم می‌کند.
    - `metaKey` {{optional_inline}}
      - : یک مقدار بولی، پیش‌فرض `false`، که مقدار {{domxref("KeyboardEvent.metaKey")}} را تنظیم می‌کند.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("KeyboardEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("KeyboardEvent")}}، رابط (interface) اشیایی که این سازنده می‌سازد.