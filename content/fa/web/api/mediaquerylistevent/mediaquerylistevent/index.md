---
title: "MediaQueryListEvent: MediaQueryListEvent() constructor"
short-title: MediaQueryListEvent()
slug: Web/API/MediaQueryListEvent/MediaQueryListEvent
page-type: web-api-constructor
browser-compat: api.MediaQueryListEvent.MediaQueryListEvent
---

{{APIRef("CSSOM view API")}}

سازنده **`MediaQueryListEvent()`** یک شیء جدید از نوع {{domxref("MediaQueryListEvent")}} می‌سازد.

## Syntax

```js-nolint
new MediaQueryListEvent(type)
new MediaQueryListEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد را مشخص می‌کند. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را `change` قرار می‌دهند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `media` {{optional_inline}}
      - : یک رشته که یک پرسش رسانه‌ای (media query) سریالی‌شده را نشان می‌دهد. مقدار پیش‌فرض آن `""` است.
    - `matches` {{optional_inline}}
      - : یک مقدار بولی که وضعیت پرسش رسانه‌ای را نشان می‌دهد؛ `true` اگر مطابقت داشته باشد و `false` اگر نداشته باشد. مقدار پیش‌فرض آن `false` است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("MediaQueryListEvent")}}.

## مثال‌ها

```js
const media = "(width <= 600px)";
const matches = true;

const myMediaQueryListEvent = new MediaQueryListEvent("change", {
  media,
  matches,
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [پرسش‌های رسانه‌ای (Media queries)](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از پرسش‌های رسانه‌ای در کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}