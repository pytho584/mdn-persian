---
title: "Navigation: currententrychange event"
short-title: currententrychange
slug: Web/API/Navigation/currententrychange_event
page-type: web-api-event
browser-compat: api.Navigation.currententrychange_event
---

{{APIRef("Navigation API")}}

رویداد **`currententrychange`** از رابط {{domxref("Navigation")}} زمانی فعال می‌شود که {{domxref("Navigation.currentEntry")}} تغییر کرده باشد.

این رویداد در موارد زیر فعال خواهد شد:

- پیمایش‌های درون‌سندی (مانند `back()` یا `traverseTo()`).
- جایگزینی‌ها (یعنی فراخوانی `navigate()` با `history` تنظیم شده به `replace`).
- سایر فراخوانی‌هایی که وضعیت ورودی را تغییر می‌دهند (مانند `updateCurrentEntry()` یا `History.replaceState()` از API تاریخچه).

این رویداد پس از قطعی شدن پیمایش (committed) فعال می‌شود، به این معنا که URL قابل مشاهده تغییر کرده و به‌روزرسانی {{domxref("NavigationHistoryEntry")}} انجام شده است. این رویداد برای مهاجرت از استفاده از ویژگی‌های API قدیمی مانند رویدادهای `hashchange` یا `popstate` مفید است.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("currententrychange", (event) => { })

oncurrententrychange = (event) => { }
```

## نوع رویداد

یک {{domxref("NavigationCurrentEntryChangeEvent")}}. به ارث‌برده از {{domxref("Event")}}.

{{InheritanceDiagram("NavigationCurrentEntryChangeEvent")}}

## مثال‌ها

گزارش‌دهی داده‌های پیمایش:

```js
navigation.addEventListener("currententrychange", () => {
  const data = navigation.currentEntry.getState();
  submitAnalyticsData(data.analytics);
});
```

تنظیم یک رویداد به ازای هر ورودی:

```js
navigation.addEventListener("currententrychange", () => {
  navigation.currentEntry.addEventListener("dispose", genericDisposeHandler);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)