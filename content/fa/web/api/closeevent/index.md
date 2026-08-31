---
title: CloseEvent
slug: Web/API/CloseEvent
page-type: web-api-interface
browser-compat: api.CloseEvent
---

{{APIRef("Websockets API")}}{{AvailableInWorkers}}

یک `CloseEvent` زمانی به کلاینتهایی که از {{Glossary("WebSockets")}} استفاده میکنند ارسال میشود که اتصال بسته شود. این رویداد به شنوندهای که در ویژگی `onclose` شیء `WebSocket` مشخص شده تحویل داده میشود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CloseEvent.CloseEvent", "CloseEvent()")}}
  - : یک `CloseEvent` جدید ایجاد میکند.

## ویژگیهای نمونه

_این رابط همچنین ویژگیهای والد خود، {{domxref("Event")}} را به ارث میبرد._

- {{domxref("CloseEvent.code")}} {{ReadOnlyInline}}
  - : یک `unsigned short` شامل کد بستن اتصال را برمیگرداند.
- {{domxref("CloseEvent.reason")}} {{ReadOnlyInline}}
  - : رشتهای برمیگرداند که دلیل بسته شدن اتصال توسط سرور را نشان میدهد. این مقدار به سرور و زیرپروتکل خاص بستگی دارد.
- {{domxref("CloseEvent.wasClean")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمیگرداند که نشان میدهد آیا اتصال بهطور تمیز بسته شده است یا خیر.

## روشهای نمونه

_این رابط همچنین روشهای والد خود، {{domxref("Event")}} را به ارث میبرد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebSocket")}}