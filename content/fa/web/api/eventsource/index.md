---
title: EventSource
slug: Web/API/EventSource
page-type: web-api-interface
browser-compat: api.EventSource
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

رابط **`EventSource`** درگاه محتوای وب به [رویدادهای ارسال‌شده از سمت سرور](/en-US/docs/Web/API/Server-sent_events) است.

یک نمونه از `EventSource` یک اتصال پایدار به یک سرور [HTTP](/en-US/docs/Web/HTTP) باز می‌کند که رویدادها را در قالب `text/event-stream` ارسال می‌کند. این اتصال تا زمانی که با فراخوانی {{domxref("EventSource.close()")}} بسته نشود، باز می‌ماند.

{{InheritanceDiagram}}

هنگامی که اتصال برقرار شد، پیام‌های دریافتی از سرور در قالب رویداد به کد شما تحویل داده می‌شوند. اگر پیام دریافتی دارای فیلد `event` باشد، رویداد فعال‌شده همان مقدار آن فیلد است. اگر فیلد `event` وجود نداشته باشد، یک رویداد {{domxref("EventSource/message_event", "message")}} عمومی صادر می‌شود.

برخلاف [WebSockets](/en-US/docs/Web/API/WebSockets_API)، رویدادهای ارسال‌شده از سمت سرور یک‌طرفه هستند؛ یعنی پیام‌های داده فقط در یک جهت، از سرور به کلاینت (مانند مرورگر وب کاربر)، ارسال می‌شوند. همین ویژگی آن‌ها را به گزینه‌ای بسیار مناسب تبدیل می‌کند وقتی نیازی به ارسال داده از سمت کلاینت به سرور در قالب پیام وجود ندارد. برای مثال، `EventSource` رویکردی مفید برای مدیریت چیزهایی مانند به‌روزرسانی وضعیت شبکه‌های اجتماعی، خوراک‌های خبری، یا انتقال داده به سازوکار ذخیره‌سازی سمت کلاینت مانند [IndexedDB](/en-US/docs/Web/API/IndexedDB_API) یا [web storage](/en-US/docs/Web/API/Web_Storage_API) است.

> [!WARNING]
> وقتی از **HTTP/2 استفاده نشود**، SSE با محدودیت حداکثر تعداد اتصال‌های باز مواجه است؛ این محدودیت به‌ویژه زمانی آزاردهنده است که تب‌های مختلفی باز می‌کنید، چون سقف مجاز _به‌ازای هر مرورگر_ است و عدد بسیار کمی (۶) تعیین شده است. این مشکل در [Chrome](https://crbug.com/275955) و [Firefox](https://bugzil.la/906896) با وضعیت «Won't fix» (قابل اصلاح نیست) علامت‌گذاری شده است. این محدودیت به‌ازای هر مرورگر + دامنه اعمال می‌شود؛ یعنی می‌توانید در همه تب‌ها ۶ اتصال SSE به `www.example1.com` و ۶ اتصال SSE جداگانه به `www.example2.com` باز کنید (برگرفته از [Stack Overflow](https://stackoverflow.com/questions/5195452/websockets-vs-server-sent-events-eventsource/5326159)). هنگام استفاده از HTTP/2، حداکثر تعداد _جریان‌های HTTP_ همزمان بین سرور و کلاینت توافق می‌شود (پیش‌فرض ۱۰۰).

## سازنده

- {{domxref("EventSource.EventSource", "EventSource()")}}
  - : یک `EventSource` جدید برای دریافت رویدادهای ارسال‌شده از سمت سرور از یک URL مشخص می‌سازد؛ به صورت اختیاری در حالت credentials (اعتبارنامه).

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("EventSource.readyState")}} {{ReadOnlyInline}}
  - : عددی که وضعیت اتصال را نشان می‌دهد. مقادیر ممکن عبارت‌اند از `CONNECTING` (`0`)، `OPEN` (`1`) یا `CLOSED` (`2`).
- {{domxref("EventSource.url")}} {{ReadOnlyInline}}
  - : رشته‌ای که URL منبع رویداد را نشان می‌دهد.
- {{domxref("EventSource.withCredentials")}} {{ReadOnlyInline}}
  - : مقدار بولی که مشخص می‌کند آیا شیء `EventSource` با اعتبارنامه‌های متقاطع-مبدأ ([CORS](/en-US/docs/Web/HTTP/Guides/CORS)) ساخته شده است (`true`) یا نه (`false`، پیش‌فرض).

## متدهای نمونه

_این رابط همچنین متدهای والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("EventSource.close()")}}
  - : اگر اتصالی برقرار باشد، آن را می‌بندد و ویژگی `readyState` را روی `CLOSED` تنظیم می‌کند. اگر اتصال از قبل بسته شده باشد، این متد هیچ کاری انجام نمی‌دهد.

## رویدادها

- {{domxref("EventSource/error_event", "error")}}
  - : زمانی صادر می‌شود که اتصال به یک منبع رویداد باز نشود.
- {{domxref("EventSource/message_event", "message")}}
  - : زمانی صادر می‌شود که داده‌ای از یک منبع رویداد دریافت شود.
- {{domxref("EventSource/open_event", "open")}}
  - : زمانی صادر می‌شود که اتصال به یک منبع رویداد باز شده باشد.

علاوه بر این، خود منبع رویداد ممکن است پیام‌هایی با فیلد `event` ارسال کند که رویدادهای موردی (ad hoc) کلیدخورده با همان مقدار ایجاد می‌کنند.

## مثال‌ها

در این مثال ساده، یک `EventSource` برای دریافت رویدادهای بدون نام از سرور ساخته شده است؛ صفحه‌ای با نام `sse.php` مسئول تولید این رویدادهاست.

```js
const evtSource = new EventSource("sse.php");
const eventList = document.querySelector("ul");

evtSource.onmessage = (e) => {
  const newElement = document.createElement("li");

  newElement.textContent = `message: ${e.data}`;
  eventList.appendChild(newElement);
};
```

هر رویداد دریافتی باعث اجرای هندلر رویداد `onmessage` در شیء `EventSource` ما می‌شود. این هندلر به نوبه خود یک عنصر جدید {{HTMLElement("li")}} می‌سازد، داده پیام را در آن می‌نویسد و عنصر جدید را به عنصر فهرست موجود در سند اضافه می‌کند.

> [!NOTE]
> می‌توانید یک مثال کامل را روی GitHub ببینید — [Simple SSE demo using PHP](https://github.com/mdn/dom-examples/tree/main/server-sent-events).

برای گوش دادن به رویدادهای نام‌دار، باید برای هر نوع رویداد ارسالی یک شنونده (listener) داشته باشید.

```js
const sse = new EventSource("/api/v1/sse");

/*
 * This will listen only for events
 * similar to the following:
 *
 * event: notice
 * data: useful data
 * id: some-id
 */
sse.addEventListener("notice", (e) => {
  console.log(e.data);
});

/*
 * Similarly, this will listen for events
 * with the field `event: update`
 */
sse.addEventListener("update", (e) => {
  console.log(e.data);
});

/*
 * The event "message" is a special case, as it
 * will capture events without an event field
 * as well as events that have the specific type
 * `event: message` It will not trigger on any
 * other event type.
 */
sse.addEventListener("message", (e) => {
  console.log(e.data);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویدادهای ارسال‌شده از سمت سرور](/en-US/docs/Web/API/Server-sent_events)
- [استفاده از رویدادهای ارسال‌شده از سمت سرور](/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)