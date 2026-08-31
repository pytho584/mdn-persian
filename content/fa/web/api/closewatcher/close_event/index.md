---
title: "CloseWatcher: close event"
short-title: close
slug: Web/API/CloseWatcher/close_event
page-type: web-api-event
browser-compat: api.CloseWatcher.close_event
---

{{APIRef("HTML DOM")}}

یک رویداد `close` روی یک شیء {{domxref("CloseWatcher")}} هنگامی که یک درخواست بستن دریافت شود، شلیک می‌شود و تنها در صورتی شلیک می‌شود که رویداد {{domxref("CloseWatcher.cancel_event", "cancel")}} که قبل از `close` رخ داده است، لغو نشده باشد.

کنترل‌کننده رویداد `close` جایی است که کد مربوط به بستن مؤلفه رابط کاربری باید فراخوانی شود: این کار تضمین می‌کند که مؤلفه چه از طریق سیگنال بستن مختص پلتفرم و چه از طریق فراخوانی {{domxref("CloseWatcher.requestClose()")}} به درستی بسته خواهد شد.

## نحو

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("close", (event) => { })

onclose = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مثال‌ها

### استفاده از رویداد `close`

از `close` برای گوش دادن به درخواست‌های بستن استفاده کنید.

```js
watcher.addEventListener("close", () => {
  // Close your UI component
  sidebar.hide();
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}