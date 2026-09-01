---
title: "Element: webkitmouseforceup event"
short-title: webkitmouseforceup
slug: Web/API/Element/webkitmouseforceup_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.webkitmouseforceup_event
---

{{APIRef("Force Touch Events")}}{{Non-standard_header}}

رویداد غیراستاندارد **`webkitmouseforceup`** توسط سافاری در یک {{domxref("Element")}} مدتی پس از رویداد {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}} فعال میشود، زمانی که فشار روی دکمه به اندازهای کاهش یابد که «کلیک فشاری» (force click) پایان یابد.

**`webkitmouseforceup`** یک رویداد اختصاصی و مخصوص WebKit است. این رویداد بخشی از قابلیت [رویدادهای Force Touch](/en-US/docs/Web/API/Force_Touch_events) محسوب میشود.

## نحو (Syntax)

برای استفاده از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا برای تنظیم یک ویژگی مدیریت رویداد (event handler property) از آن استفاده کنید.

```js-nolint
addEventListener("webkitmouseforceup", (event) => { })

onwebkitmouseforceup = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث رسیده است.

{{InheritanceDiagram("MouseEvent")}}

## مشخصات (Specifications)

_جزء هیچ مشخصاتی نیست._ اپل [توضیحاتی در Mac Developer Library](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/SafariJSProgTopics/RespondingtoForceTouchEventsfromJavaScript.html) ارائه کرده است.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمهای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/webkitmouseforcewillbegin_event", "webkitmouseforcewillbegin")}}
- {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}}
- {{domxref("Element/webkitmouseforcechanged_event", "webkitmouseforcechanged")}}