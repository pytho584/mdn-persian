---
title: HashChangeEvent
slug: Web/API/HashChangeEvent
page-type: web-api-interface
browser-compat: api.HashChangeEvent
---

{{APIRef("HTML DOM")}}

رابطه‌ی **`HashChangeEvent`** رویدادهایی را نشان می‌دهد که وقتی شناسه‌ی قطعه (fragment identifier) از URL تغییر می‌کند، رخ می‌دهند.

شناسه‌ی قطعه بخشی از URL است که بعد از نماد `#` می‌آید و آن را نیز شامل می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("HashChangeEvent.HashChangeEvent", "HashChangeEvent()")}}
  - : یک شیء جدید `HashChangeEvent` می‌سازد.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های والد خود، {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("HashChangeEvent.newURL")}} {{ReadOnlyInline}}
  - : URL جدیدی که پنجره به سمت آن در حال ناوبری است.
- {{domxref("HashChangeEvent.oldURL")}} {{ReadOnlyInline}}
  - : URL قبلی که پنجره از آن ناوبری شده بود.

## روش‌های نمونه

_این رابط روش خاص خود را ندارد، اما روش‌های والد خود، {{domxref("Event")}} را به ارث می‌برد._

## مثال‌ها

### مثال پایه

```js
function locationHashChanged() {
  if (location.hash === "#some-cool-feature") {
    someCoolFeature();
  }
}

window.addEventListener("hashchange", locationHashChanged);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## رویدادهای مرتبط

- {{domxref("window.hashchange_event", "hashchange")}}
- {{domxref("window.popstate_event", "popstate")}}