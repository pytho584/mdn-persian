---
title: "BufferedChangeEvent: BufferedChangeEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BufferedChangeEvent/BufferedChangeEvent"
translated_by: "n8n + AI"
---

---
title: "BufferedChangeEvent: BufferedChangeEvent() constructor"
short-title: BufferedChangeEvent()
slug: Web/API/BufferedChangeEvent/BufferedChangeEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.BufferedChangeEvent.BufferedChangeEvent
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

سازندهٔ **`BufferedChangeEvent()`** از رابط {{domxref("BufferedChangeEvent")}} یک نمونهٔ شیء `BufferedChangeEvent` جدید ایجاد می‌کند.

## سینتکس

```js-nolint
new BufferedChangeEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نوع رویداد را مشخص می‌کند. در مورد `BufferedChangeEvent` این مقدار همیشه `bufferedchange` است.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، ویژگی‌های زیر را دارد:

    > [!NOTE]
    > اگرچه مشخصات، `options` را اختیاری تعیین کرده، اما سافاری (در حال حاضر تنها پیاده‌سازی) اگر آرگومان کاملاً حذف شود، یک `TypeError` پرتاب می‌کند. ارسال یک شیء خالی (`{}`) به‌درستی کار می‌کند.
    - `addedRanges` {{optional_inline}}
      - : یک شیء {{domxref("TimeRanges")}} که بازه‌های زمانی اضافه‌شده به بافر را نشان می‌دهد.
    - `removedRanges` {{optional_inline}}
      - : یک شیء {{domxref("TimeRanges")}} که بازه‌های زمانی حذف‌شده از بافر را نشان می‌دهد.

### مقدار بازگشتی

یک نمونهٔ شیء جدید از {{domxref("BufferedChangeEvent")}}.

## مثال‌ها

### بررسی یک رویداد bufferedchange

سازندهٔ `BufferedChangeEvent()` معمولاً به‌صورت دستی فراخوانی نمی‌شود. وقتی رویداد `bufferedchange` یک {{domxref("ManagedSourceBuffer")}} رخ می‌دهد (به این معنی که بازه‌های بافرشده آن تغییر می‌کنند)، مرورگر یک شیء `BufferedChangeEvent` به‌عنوان شیء رویداد می‌سازد.

ویژگی‌های رویداد توصیف می‌کنند چه چیزی تغییر کرده است:

```js
sourceBuffer.addEventListener("bufferedchange", (event) => {
  console.log(event instanceof BufferedChangeEvent); // true
  console.log(event.type); // "bufferedchange"
  console.log(event.addedRanges); // TimeRanges — ranges added to the buffer
  console.log(event.removedRanges); // TimeRanges — ranges removed from the buffer
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ManagedSourceBuffer")}}
- رویداد {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}}