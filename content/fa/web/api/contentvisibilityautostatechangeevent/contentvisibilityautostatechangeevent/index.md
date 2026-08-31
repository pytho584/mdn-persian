---
title: "ContentVisibilityAutoStateChangeEvent: ContentVisibilityAutoStateChangeEvent() constructor"
---

---
title: "ContentVisibilityAutoStateChangeEvent: ContentVisibilityAutoStateChangeEvent() constructor"
short-title: ContentVisibilityAutoStateChangeEvent()
slug: Web/API/ContentVisibilityAutoStateChangeEvent/ContentVisibilityAutoStateChangeEvent
page-type: web-api-constructor
browser-compat: api.ContentVisibilityAutoStateChangeEvent.ContentVisibilityAutoStateChangeEvent
---

{{APIRef("CSS Containment")}}

سازندهی **`ContentVisibilityAutoStateChangeEvent()`** یک نمونهی جدید از شیء {{domxref("ContentVisibilityAutoStateChangeEvent")}} می‌سازد.

## سینتکس

```js-nolint
new ContentVisibilityAutoStateChangeEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است که نوع رویداد را نشان می‌دهد. در مورد `ContentVisibilityAutoStateChangeEvent`، این مقدار همیشه `event` است.
- `options` {{optional_inline}}
  - : شیئی است که دارای ویژگی‌های زیر است:
    - `skipped`
      - : یک مقدار بولی است که اگر عامل کاربر [از محتویات عنصر صرف‌نظر کند](/en-US/docs/Web/CSS/Guides/Containment/Using#skips_its_contents)، مقدار آن `true` و در غیر این صورت `false` است.

## مثال‌ها

یک توسعه‌دهنده به‌صورت دستی از این سازنده استفاده نمی‌کند. بلکه، یک شیء جدید `ContentVisibilityAutoStateChangeEvent` زمانی ساخته می‌شود که یک کنترل‌کننده در نتیجه‌ی فعال شدن رویداد {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}} فراخوانده شود.

```js
canvasElem.addEventListener("contentvisibilityautostatechange", (event) => {
  // …
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}}
- [محدودسازی CSS](/en-US/docs/Web/CSS/Guides/Containment)
- ویژگی {{cssxref("content-visibility")}}
- ویژگی {{cssxref("contain")}}