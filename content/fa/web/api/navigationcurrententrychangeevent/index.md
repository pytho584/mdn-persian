---
title: NavigationCurrentEntryChangeEvent
slug: Web/API/NavigationCurrentEntryChangeEvent
page-type: web-api-interface
browser-compat: api.NavigationCurrentEntryChangeEvent
---

{{APIRef("Navigation API")}}

رابطِ **`NavigationCurrentEntryChangeEvent`** در {{domxref("Navigation API", "Navigation API", "", "nocode")}}، شیء رخداد (event object) برای رویداد {{domxref("Navigation/currententrychange_event", "currententrychange")}} است که زمانی رخ می‌دهد که {{domxref("Navigation.currentEntry")}} تغییر کرده باشد.

این رویداد برای ناوبری‌های همان سند (مثلاً {{domxref("Navigation.back", "back()")}} یا {{domxref("Navigation.traverseTo", "traverseTo()")}})، جایگزینی‌ها (یعنی فراخوانی {{domxref("Navigation.navigate", "navigate()")}} با مقدار `history` برابر با `replace`)، یا سایر فراخوانی‌هایی که وضعیت (state) ورودی را تغییر می‌دهند (مانند {{domxref("Navigation.updateCurrentEntry", "updateCurrentEntry()")}} یا {{domxref("History.replaceState()")}} در {{domxref("History API", "History API", "", "nocode")}})، رخ می‌دهد.

این رویداد پس از قطعی‌شدن ناوبری رخ می‌دهد؛ یعنی URL قابل مشاهده تغییر کرده و به‌روزرسانی {{domxref("NavigationHistoryEntry")}} انجام شده است. این رویداد برای مهاجرت از استفاده از قابلیت‌های قدیمی‌تر API مانند رویدادهای {{domxref("Window/hashchange_event", "hashchange")}} یا {{domxref("Window/popstate_event", "popstate")}} مفید است.

{{InheritanceDiagram}}

## سازنده

- {{domxref("NavigationCurrentEntryChangeEvent.NavigationCurrentEntryChangeEvent", "NavigationCurrentEntryChangeEvent()")}}
  - : یک نمونه شیء جدید از `NavigationCurrentEntryChangeEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های زیر را از والد خود، {{DOMxRef("Event")}}، به ارث می‌برد._

- {{domxref("NavigationCurrentEntryChangeEvent.from", "from")}} {{ReadOnlyInline}}
  - : نمونه {{domxref("NavigationHistoryEntry")}}ای را برمی‌گرداند که از آن ناوبری انجام شده است.
- {{domxref("NavigationCurrentEntryChangeEvent.navigationType", "navigationType")}} {{ReadOnlyInline}}
  - : نوع ناوبری که منجر به تغییر شده را برمی‌گرداند.

## مثال‌ها

گزارش داده‌های ناوبری:

```js
navigation.addEventListener("currententrychange", () => {
  const data = navigation.currentEntry.getState();
  submitAnalyticsData(data.analytics);
});
```

ایجاد یک رویداد به‌ازای هر ورودی:

```js
navigation.addEventListener("currententrychange", () => {
  navigation.currentEntry.addEventListener("dispose", genericDisposeHandler);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)
- [دموی زنده‌ی Navigation API](https://mdn.github.io/dom-examples/navigation-api/) ([مشاهده سورس دمو](https://github.com/mdn/dom-examples/tree/main/navigation-api))