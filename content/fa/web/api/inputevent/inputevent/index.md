---
title: "InputEvent: InputEvent() constructor"
short-title: InputEvent()
slug: Web/API/InputEvent/InputEvent
page-type: web-api-constructor
browser-compat: api.InputEvent.InputEvent
---

{{APIRef("UI Events")}}

سازندهٔ **`InputEvent()`** یک شیء جدید {{domxref("InputEvent")}} می‌سازد.

## Syntax

```js-nolint
new InputEvent(type)
new InputEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد.
    این رشته به بزرگی/کوچکی حروف حساس است و مرورگرها آن را روی `beforeinput` یا `input` قرار می‌دهند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("UIEvent/UIEvent", "UIEvent()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `inputType` {{optional_inline}}
      - : رشته‌ای که نوع تغییر در محتوای قابل ویرایش را مشخص می‌کند؛
        مانند درج، حذف یا قالب‌بندی متن.
    - `data` {{optional_inline}}
      - : رشته‌ای شامل نویسه‌هایی که باید درج شوند.
        اگر تغییر متنی را درج نکند (مثلاً هنگام حذف نویسه‌ها)، این رشته می‌تواند خالی باشد.
    - `isComposing` {{optional_inline}}
      - : یک مقدار بولین که نشان می‌دهد رویداد بخشی از یک نشست ترکیب (composition) است؛
        یعنی بعد از رویداد {{domxref("Element/compositionstart_event", "compositionstart")}} و قبل از رویداد {{domxref("Element/compositionend_event", "compositionend")}} رخ داده است. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک شیء جدید {{domxref("InputEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("InputEvent")}}، رابطِ اشیایی که این سازنده می‌سازد.