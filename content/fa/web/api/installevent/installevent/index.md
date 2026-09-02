---
title: "InstallEvent: سازنده InstallEvent()"
short-title: InstallEvent()
slug: Web/API/InstallEvent/InstallEvent
page-type: web-api-constructor
browser-compat: api.InstallEvent.InstallEvent
---

{{APIRef("Service Workers API")}}

سازنده **`InstallEvent()`** یک شیء جدید از نوع {{domxref("InstallEvent")}} ایجاد می‌کند.

## نحو

```js-nolint
new InstallEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته شامل نام رویداد. این رشته به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را به `install` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند شامل هر تنظیمات سفارشی دیگری باشد که می‌خواهید به شیء رویداد اعمال کنید. در حال حاضر هیچ گزینه اجباری وجود ندارد، اما این برای سازگاری با آینده تعریف شده است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("InstallEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("Promise")}}
- [API Fetch](/en-US/docs/Web/API/Fetch_API)