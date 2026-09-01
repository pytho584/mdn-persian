---
title: "Element: webkitmouseforcechanged event"
short-title: webkitmouseforcechanged
slug: Web/API/Element/webkitmouseforcechanged_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.webkitmouseforcechanged_event
---

{{APIRef("Force Touch Events")}}{{Non-standard_header}}

رویداد غیراستاندارد **`webkitmouseforcechanged`** هر بار که مقدار فشار روی ترک‌پد یا صفحه لمسی تغییر می‌کند، توسط Safari فعال می‌شود.

**`webkitmouseforcechanged`** یک رویداد اختصاصی و مخصوص WebKit است که توسط Apple برای پشتیبانی از ویژگی [Force Touch events](/en-US/docs/Web/API/Force_Touch_events) معرفی شده است.

این رویداد ابتدا پس از رویداد {{domxref("Element/mousedown_event", "mousedown")}} فعال می‌شود و قبل از رویداد {{domxref("Element/mouseup_event", "mouseup")}} از فعال شدن بازمی‌ایستد.

## نحو (Syntax)

برای استفاده از این رویداد، نام آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("webkitmouseforcechanged", (event) => { })

onwebkitmouseforcechanged = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. این رویداد از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("MouseEvent")}}

## مشخصات

_بخشی از هیچ مشخصاتی نیست._ Apple [شرحی را در کتابخانه توسعه‌دهندگان Mac](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/SafariJSProgTopics/RespondingtoForceTouchEventsfromJavaScript.html) ارائه کرده است.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: آشنایی با رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/webkitmouseforcewillbegin_event", "webkitmouseforcewillbegin")}}
- {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}}
- {{domxref("Element/webkitmouseforceup_event", "webkitmouseforceup")}}