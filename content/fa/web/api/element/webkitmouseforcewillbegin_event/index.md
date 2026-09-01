---
title: "Element: webkitmouseforcewillbegin event"
short-title: webkitmouseforcewillbegin
slug: Web/API/Element/webkitmouseforcewillbegin_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.Element.webkitmouseforcewillbegin_event
---

{{APIRef("Force Touch Events")}}{{Non-standard_header}}

سافاری در macOS، رویداد غیراستاندارد **`webkitmouseforcewillbegin`** را روی یک {{domxref("Element")}} پیش از فعال‌سازی رویداد اولیه {{domxref("Element/mousedown_event", "mousedown")}} صادر می‌کند.

این رویداد فرصتی فراهم می‌کند تا به سیستم اعلام کنید که در صورت تبدیل شدن کلیک به [رویدادهای Force Touch](/en-US/docs/Web/API/Force_Touch_events)، هیچ‌یک از اقدامات پیش‌فرض Force Touch فعال نشوند.

برای اینکه به macOS بگویید در صورتی که کاربر فشار کافی برای فعال‌سازی رویداد Force Touch اعمال کند، هیچ اقدام پیش‌فرضی از نوع Force Touch انجام ندهد، متد {{domxref("Event.preventDefault", "preventDefault()")}} را روی شیء رویداد `webkitmouseforcewillbegin` فراخوانی کنید.

**`webkitmouseforcewillbegin`** یک رویداد اختصاصی و مخصوص WebKit است. این رویداد بخشی از قابلیت [رویدادهای Force Touch](/en-US/docs/Web/API/Force_Touch_events) محسوب می‌شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگی handler رویداد، از الگوی زیر استفاده کنید:

```js-nolint
addEventListener("webkitmouseforcewillbegin", (event) => { })

onwebkitmouseforcewillbegin = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("MouseEvent")}}

## مشخصات

_مشخصات خاصی برای این رویداد وجود ندارد._ اپل [توضیحاتی در Mac Developer Library](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/SafariJSProgTopics/RespondingtoForceTouchEventsfromJavaScript.html) ارائه کرده است.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [یادگیری: آشنایی با رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}}
- {{domxref("Element/webkitmouseforceup_event", "webkitmouseforceup")}}
- {{domxref("Element/webkitmouseforcechanged_event", "webkitmouseforcechanged")}}