---
title: "IDBVersionChangeEvent: IDBVersionChangeEvent() constructor"
short-title: IDBVersionChangeEvent()
slug: Web/API/IDBVersionChangeEvent/IDBVersionChangeEvent
page-type: web-api-constructor
browser-compat: api.IDBVersionChangeEvent.IDBVersionChangeEvent
---

{{securecontext_header}}{{APIRef("IndexedDB")}}

سازنده **`IDBVersionChangeEvent()`** یک شیء جدید {{domxref("IDBVersionChangeEvent")}} ایجاد می‌کند که برای نمایش تغییر نسخه پایگاه داده، در نتیجه کنترل‌کننده رویداد {{domxref('IDBOpenDBRequest.upgradeneeded_event', 'onupgradeneeded')}} استفاده می‌شود.

## Syntax

```js-nolint
new IDBVersionChangeEvent(type)
new IDBVersionChangeEvent(type, options)
```

### Parameters

- `type`
  - : یک رشته با نام رویداد. به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `versionchange`، `success` یا `blocked` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `oldVersion` {{optional_inline}}
      - : یک عدد که نسخه قبلی پایگاه داده را نشان می‌دهد. مقدار پیش‌فرض آن `0` است.
    - `newVersion` {{optional_inline}}
      - : یک عدد صحیح بدون علامت (unsigned long) که نسخه جدید پایگاه داده را نشان می‌دهد، یا اگر پایگاه داده در حال حذف شدن است `null` باشد. مقدار پیش‌فرض آن `null` است.

### Return value

یک شیء جدید {{domxref("IDBVersionChangeEvent")}}.

## Examples

برای یک مثال کامل کار شده، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}