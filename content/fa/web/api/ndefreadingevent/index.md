---
title: "NDEFReadingEvent"
---

---
title: NDEFReadingEvent
slug: Web/API/NDEFReadingEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NDEFReadingEvent
---

{{APIRef("Web NFC API")}}{{securecontext_header}}{{SeeCompatTable}}

رابط **`NDEFReadingEvent`** در [Web NFC API](/en-US/docs/Web/API/Web_NFC_API) نشان‌دهنده رویدادهایی است که وقتی {{DOMxRef("NDEFReader")}} خوانش‌های جدید NFC را به دست می‌آورد، ارسال می‌شوند.

{{InheritanceDiagram}}

## سازنده

- {{DOMxRef("NDEFReadingEvent.NDEFReadingEvent", "NDEFReadingEvent.NDEFReadingEvent()")}} {{Experimental_Inline}}
  - : یک `NDEFReadingEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های خود را از والدش، {{DOMxRef("Event")}}، به ارث می‌برد._

- {{DOMxRef("NDEFReadingEvent.message")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{DOMxRef("NDEFMessage")}} حاوی پیام دریافتی را برمی‌گرداند.
- {{DOMxRef("NDEFReadingEvent.serialNumber")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شماره سریال دستگاه را برمی‌گرداند؛ این شماره برای جلوگیری از برخورد (anti-collision) و شناسایی استفاده می‌شود. اگر شماره سریالی موجود نباشد، رشته خالی برمی‌گرداند.

## متدهای نمونه

_متدهای خود را از والدش، {{DOMxRef("Event")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}