---
title: "Element: webkitmouseforcedown event"
short-title: webkitmouseforcedown
slug: Web/API/Element/webkitmouseforcedown_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.webkitmouseforcedown_event
---

{{APIRef("Force Touch Events")}}{{Non-standard_header}}

پس از آن که یک رویداد {{domxref("Element.mousedown_event", "mousedown")}} در عنصر شلیک شود، اگر و هنگامی که فشار کافی به دکمه ماوس یا ترک‌پد وارد شود تا به عنوان یک «کلیک فشاری» (force click) محسوب گردد، سافاری شروع به ارسال رویدادهای **`webkitmouseforcedown`** به آن عنصر می‌کند.

**`webkitmouseforcedown`** یک رویداد اختصاصی و مخصوص WebKit است. این رویداد بخشی از قابلیت [رویدادهای فورس تاچ (Force Touch)](/en-US/docs/Web/API/Force_Touch_events) می‌باشد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم نمایید.

```js-nolint
addEventListener("webkitmouseforcedown", (event) => { })

onwebkitmouseforcedown = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MouseEvent")}}

## مشخصات (Specifications)

_جزئی از هیچ مشخصاتی نیست._ اپل [یک توضیح در کتابخانه توسعه‌دهندگان مک](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/SafariJSProgTopics/RespondingtoForceTouchEventsfromJavaScript.html) دارد.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/webkitmouseforcewillbegin_event", "webkitmouseforcewillbegin")}}
- {{domxref("Element/webkitmouseforceup_event", "webkitmouseforceup")}}
- {{domxref("Element/webkitmouseforcechanged_event", "webkitmouseforcechanged")}}