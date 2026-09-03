---
title: "NotificationEvent: NotificationEvent() constructor"
title: "NotificationEvent: NotificationEvent() constructor"
short-title: NotificationEvent()
slug: Web/API/NotificationEvent/NotificationEvent
page-type: web-api-constructor
browser-compat: api.NotificationEvent.NotificationEvent
---

{{APIRef("Web Notifications")}}{{AvailableInWorkers("service")}}

سازنده **`NotificationEvent()`** یک شیء {{domxref("NotificationEvent")}} جدید ایجاد می‌کند.

## Syntax

```js-nolint
new NotificationEvent(type, options)
```

### Parameters

- `type`
  - : رشته‌ای با نام رویداد.
    این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها آن را روی `notificationclick` یا `notificationclose` تنظیم می‌کنند.
- `options`
  - : شیءای که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_ می‌تواند ویژگی‌های زیر را داشته باشد:
    - `notification`
      - : یک شیء {{domxref("Notification")}} که به عنوان اعلانِ رویدادِ ارسال‌شده روی آن استفاده می‌شود.
    - `action` {{optional_inline}}
      - : عملی مرتبط با اعلان. مقدار پیش‌فرض آن `""` است.

### Return value

یک شیء جدید {{domxref("NotificationEvent()")}}.

## Examples

```js
const n = new Notification("Hello");
const myNotificationEvent = new NotificationEvent(type, { notification: n });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}