---
title: "PageTransitionEvent"
---

---
title: PageTransitionEvent
slug: Web/API/PageTransitionEvent
page-type: web-api-interface
browser-compat: api.PageTransitionEvent
---

{{APIRef("HTML DOM")}}

شیء رویداد **`PageTransitionEvent`** در داخل توابع مدیریت‌کننده رویدادهای [`pageshow`](/en-US/docs/Web/API/Window/pageshow_event) و [`pagehide`](/en-US/docs/Web/API/Window/pagehide_event) در دسترس است؛ این رویدادها هنگام بارگذاری یا بارگیری‌نشدن (unload) یک سند فعال می‌شوند.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("PageTransitionEvent.PageTransitionEvent", "PageTransitionEvent()")}}
  - : یک شیء `PageTransitionEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

_این رابط همچنین ویژگی‌های والد خود، {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("PageTransitionEvent.persisted")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا سند از حافظه نهان (cache) بارگذاری شده است یا خیر.

## مثال

```js
window.addEventListener("pageshow", (event) => {
  if (event.persisted) {
    alert("The page was cached by the browser");
  } else {
    alert("The page was NOT cached by the browser");
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`pageshow`](/en-US/docs/Web/API/Window/pageshow_event)
- رویداد [`pagehide`](/en-US/docs/Web/API/Window/pagehide_event)