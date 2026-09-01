---
title: "Force Touch events"
slug: Web/API/Force_Touch_events
page-type: web-api-overview
status:
  - non-standard
---

{{DefaultAPISidebar("Force Touch Events")}}{{Non-standard_header}}

**Force Touch Events** یک ویژگی اختصاصی و مخصوص اپل است که (در صورت پشتیبانی سخت‌افزار ورودی) تعامل‌های جدیدی را بر اساس میزان فشاری که کاربر روی صفحه لمسی یا ترک‌پد کلیک می‌کند یا آن را فشار می‌دهد، ممکن می‌سازد.

## رویدادها

- {{domxref("Element/webkitmouseforcewillbegin_event", "webkitmouseforcewillbegin")}} {{non-standard_inline}}
  - : این رویداد قبل از رویداد {{domxref("Element/mousedown_event", "mousedown")}} فعال می‌شود. کاربرد اصلی آن این است که می‌توان با {{domxref("Event.preventDefault()", "default-prevented", "", 1)}} از رفتار پیش‌فرض آن جلوگیری کرد.
- {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}} {{non-standard_inline}}
  - : این رویداد پس از رویداد {{domxref("Element/mousedown_event", "mousedown")}} فعال می‌شود، به محض اینکه فشار کافی اعمال شده باشد تا به‌عنوان یک «کلیک فشاری» (force click) تلقی شود.
- {{domxref("Element/webkitmouseforceup_event", "webkitmouseforceup")}} {{non-standard_inline}}
  - : این رویداد پس از رویداد {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}} فعال می‌شود، به محض اینکه فشار به اندازه کافی کاهش یابد تا «کلیک فشاری» پایان یابد.
- {{domxref("Element/webkitmouseforcechanged_event", "webkitmouseforcechanged")}} {{non-standard_inline}}
  - : این رویداد هر بار که میزان فشار تغییر می‌کند فعال می‌شود. این رویداد ابتدا پس از رویداد {{domxref("Element/mousedown_event", "mousedown")}} فعال می‌شود و پیش از رویداد {{domxref("Element/mouseup_event", "mouseup")}} از فعال‌شدن بازمی‌ایستد.

## ویژگی‌های رویداد

ویژگی زیر بر روی آبجکت‌های رویدادهای {{domxref("Element/webkitmouseforcewillbegin_event", "webkitmouseforcewillbegin")}}، {{domxref("Element/mousedown_event", "mousedown")}}، {{domxref("Element/webkitmouseforcechanged_event", "webkitmouseforcechanged")}}، {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}}، {{domxref("Element/webkitmouseforceup_event", "webkitmouseforceup")}}، {{domxref("Element/mousemove_event", "mousemove")}} و {{domxref("Element/mouseup_event", "mouseup")}} در دسترس است:

- {{domxref("MouseEvent.webkitForce")}} {{non-standard_inline()}} {{ReadOnlyInline}}
  - : میزان فشاری که در حال حاضر به ترک‌پد یا صفحه لمسی وارد می‌شود.

## ثابت‌ها

این ثابت‌ها برای تعیین شدت نسبی فشاری که {{domxref("MouseEvent.webkitForce")}} نشان می‌دهد مفید هستند:

- {{domxref("MouseEvent.WEBKIT_FORCE_AT_MOUSE_DOWN_static", "MouseEvent.WEBKIT_FORCE_AT_MOUSE_DOWN")}} {{non-standard_inline}} {{ReadOnlyInline}}
  - : حداقل نیروی لازم برای یک کلیک معمولی.
- {{domxref("MouseEvent.WEBKIT_FORCE_AT_FORCE_MOUSE_DOWN_static", "MouseEvent.WEBKIT_FORCE_AT_FORCE_MOUSE_DOWN")}} {{non-standard_inline}} {{ReadOnlyInline}}
  - : حداقل نیروی لازم برای یک کلیک فشاری (force click).

## مشخصات

_این ویژگی بخشی از هیچ specification (مشخصات) رسمی نیست._ اپل [توضیحاتی در Mac Developer Library](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/SafariJSProgTopics/RespondingtoForceTouchEventsfromJavaScript.html) ارائه کرده است.