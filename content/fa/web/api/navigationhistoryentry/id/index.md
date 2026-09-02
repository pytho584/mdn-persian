---
title: "NavigationHistoryEntry: id property"
short-title: id
slug: Web/API/NavigationHistoryEntry/id
page-type: web-api-instance-property
browser-compat: api.NavigationHistoryEntry.id
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`id`** در رابط {{domxref("NavigationHistoryEntry")}} مقدار `id` ورودی تاریخچه را برمی‌گرداند، یا اگر سند فعلی کاملاً فعال (fully active) نباشد، یک رشته خالی. این مقدار یک شناسه یکتا و تولیدشده توسط عامل کاربر (UA) است که همیشه نمایانگر یک ورودی تاریخچه خاص است و برای مرتبط‌سازی آن با یک منبع خارجی مانند حافظه پنهان ذخیره‌سازی مفید است.

این ویژگی با {{domxref("NavigationHistoryEntry.key", "key")}} یک ورودی تاریخچه تفاوت دارد. `key` یک مقدار یکتا و تولیدشده توسط عامل کاربر است که جایگاه ورودی تاریخچه را در فهرست ورودی‌ها نشان می‌دهد، نه خود ورودی را. از آن برای پیمایش به آن جایگاه خاص از طریق {{domxref("Navigation.traverseTo()")}} استفاده می‌شود. `key` توسط ورودی‌های دیگری که جایگزین آن ورودی در فهرست می‌شوند دوباره استفاده خواهد شد (یعنی اگر {{domxref("NavigateEvent.navigationType")}} برابر با `replace` باشد).

## مقدار

رشته‌ای که `id` مربوط به {{domxref("NavigationHistoryEntry")}} را نشان می‌دهد.

## مثال‌ها

```js
const current = navigation.currentEntry;
console.log(current.id);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)