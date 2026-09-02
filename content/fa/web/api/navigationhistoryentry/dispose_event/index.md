---
title: "NavigationHistoryEntry: dispose event"
short-title: dispose
slug: Web/API/NavigationHistoryEntry/dispose_event
page-type: web-api-event
browser-compat: api.NavigationHistoryEntry.dispose_event
---

{{APIRef("Navigation API")}}

رویداد **`dispose`** از رابط {{domxref("NavigationHistoryEntry")}} زمانی فعال می‌شود که آن ورودی (entry) دیگر بخشی از فهرست ورودی‌های تاریخچه نباشد.

حذف (disposal) در موارد زیر رخ می‌دهد:

- ورودی‌های تاریخچه‌ی جلو (forward history entries) پاک می‌شوند. برای اطلاعات بیشتر مثال [Notifications on entry disposal](https://github.com/wicg/navigation-api#notifications-on-entry-disposal) را ببینید.
- کاربر تاریخچه‌ی مرورگر خود را از طریق تنظیمات یا کنترل‌های رابط کاربری موجود پاک می‌کند.
- محدودیت تاریخچه بیش از حد مجاز می‌شود. این محدودیت در جایی مشخص نشده است، اما مرورگرها معمولاً محدودیت ۵۰ صفحه برای تاریخچه دارند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("dispose", (event) => { })

ondispose = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
navigation.addEventListener("currententrychange", () => {
  navigation.currentEntry.addEventListener("dispose", disposeHandler);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)