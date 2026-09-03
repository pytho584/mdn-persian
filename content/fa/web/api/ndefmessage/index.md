---
title: "NDEFMessage"
slug: Web/API/NDEFMessage
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NDEFMessage
---

{{securecontext_header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

رابط **`NDEFMessage`** از [Web NFC API](/en-US/docs/Web/API/Web_NFC_API) محتوای یک پیام NDEF را نشان می‌دهد که از یک برچسب NFC خوانده شده یا می‌تواند روی آن نوشته شود. یک نمونه از این رابط با فراخوانی سازنده `NDEFMessage()` یا از ویژگی {{domxref("NDEFReadingEvent.message")}} که به رویداد {{domxref("NDEFReader.reading_event", "reading")}} ارسال می‌شود، به دست می‌آید.

## سازنده

- {{DOMxRef("NDEFMessage.NDEFMessage", "NDEFMessage()")}} {{Experimental_Inline}}
  - : یک شیء جدید `NDEFMessage` ایجاد می‌کند که با رکوردهای NDEF داده شده مقداردهی اولیه می‌شود.

## ویژگی‌ها

- {{DOMxRef("NDEFMessage.records")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : فهرست رکوردهای NDEF موجود در پیام را بازمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}