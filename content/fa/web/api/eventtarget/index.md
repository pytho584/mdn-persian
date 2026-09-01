---
title: EventTarget
slug: Web/API/EventTarget
page-type: web-api-interface
browser-compat: api.EventTarget
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

رابط **`EventTarget`** توسط اشیایی پیاده‌سازی می‌شود که می‌توانند رویدادها را دریافت کنند و ممکن است برای آنها شنونده داشته باشند. به عبارت دیگر، هر هدف رویدادی سه روش مرتبط با این رابط را پیاده‌سازی می‌کند.

{{domxref("Element")}} و فرزندان آن، و همچنین {{domxref("Document")}} و {{domxref("Window")}}، رایج‌ترین اهداف رویداد هستند، اما اشیای دیگر نیز می‌توانند هدف رویداد باشند. برای مثال {{domxref("IDBRequest")}}، {{domxref("AudioNode")}} و {{domxref("AudioContext")}} نیز اهداف رویداد هستند.

بسیاری از اهداف رویداد (شامل عناصر، اسناد و پنجره‌ها) همچنین از [ثبت مدیریت‌کننده‌های رویداد](/en-US/docs/Web/API/Document_Object_Model/Events#registering_event_handlers) از طریق ویژگی‌ها و صفت‌های `onevent` پشتیبانی می‌کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("EventTarget.EventTarget()", "EventTarget()")}}
  - : یک نمونه شیء جدید از `EventTarget` ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("EventTarget.addEventListener()")}}
  - : یک مدیریت‌کننده رویداد از نوع خاصی را روی `EventTarget` ثبت می‌کند.
- {{domxref("EventTarget.removeEventListener()")}}
  - : یک شنونده رویداد را از `EventTarget` حذف می‌کند.
- {{domxref("EventTarget.dispatchEvent()")}}
  - : یک رویداد را به این `EventTarget` ارسال می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [فهرست رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#event_index)
- [مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- رابط {{domxref("Event")}}