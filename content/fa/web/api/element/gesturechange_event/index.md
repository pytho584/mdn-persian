---
title: "Element: gesturechange event"
short-title: gesturechange
slug: Web/API/Element/gesturechange_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.gesturechange_event
---

{{APIRef}}{{Non-standard_header}}

رویداد **`gesturechange`** زمانی صادر می‌شود که انگشتان در حین یک ژست لمسی حرکت کنند.

این یک رویداد اختصاصی و مخصوص WebKit است.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("gesturechange", (event) => { })

ongesturechange = (event) => { }
```

## Event type

یک {{domxref("GestureEvent")}}. این رویداد از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("GestureEvent")}}

## Specifications

این رویداد بخشی از هیچ مشخصات استانداردی نیست.

## Browser compatibility

{{Compat}}

## See also

- [مرجع کلاس GestureEvent در کتابخانه توسعه‌دهندگان Safari](https://developer.apple.com/documentation/webkitjs/gestureevent)