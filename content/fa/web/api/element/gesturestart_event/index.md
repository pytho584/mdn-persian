---
title: "Element: gesturestart event"
---

---
title: "Element: gesturestart event"
short-title: gesturestart
slug: Web/API/Element/gesturestart_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.gesturestart_event
---

{{APIRef}}{{Non-standard_header}}

رویداد **`gesturestart`** زمانی صادر می‌شود که چند انگشت با سطح لمسی تماس برقرار کنند و در نتیجه یک ژست جدید شروع شود. در طول ژست، رویدادهای {{domxref("Element/gesturechange_event", "gesturechange")}} صادر خواهند شد. وقتی ژست به پایان برسد، رویداد {{domxref("Element/gestureend_event", "gestureend")}} صادر می‌شود.

این یک رویداد اختصاصی مخصوص WebKit است.

## نحو

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد را تنظیم کنید.

```js-nolint
addEventListener("gesturestart", (event) => { })

ongesturestart = (event) => { }
```

## نوع رویداد

یک {{domxref("GestureEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("GestureEvent")}}

## مشخصات

بخشی از هیچ مشخصه‌ای نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مرجع کلاس GestureEvent در کتابخانه توسعه‌دهندگان Safari](https://developer.apple.com/documentation/webkitjs/gestureevent)