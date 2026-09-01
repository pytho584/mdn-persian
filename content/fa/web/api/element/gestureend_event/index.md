---
title: "Element: gestureend event"
short-title: gestureend
slug: Web/API/Element/gestureend_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.gestureend_event
---

{{APIRef}}{{Non-standard_header}}

رویداد **`gestureend`** زمانی فعال می‌شود که دیگر چند انگشت با سطح لمسی در تماس نباشند و بدین ترتیب ژست (gesture) پایان می‌یابد.

این یک رویداد اختصاصی مخصوص WebKit است.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler) را تنظیم کنید.

```js-nolint
addEventListener("gestureend", (event) => { })

ongestureend = (event) => { }
```

## نوع رویداد

یک {{domxref("GestureEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("GestureEvent")}}

## مشخصات

این رویداد بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [GestureEventClassReference at the Safari Developer Library](https://developer.apple.com/documentation/webkitjs/gestureevent)