---
title: PresentationConnection
slug: Web/API/PresentationConnection
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PresentationConnection
---

{{SeeCompatTable}}{{securecontext_header}}{{APIRef("Presentation API")}}

رابط `PresentationConnection` متعلق به [Presentation API](/en-US/docs/Web/API/Presentation_API) است و متدها و ویژگی‌هایی را برای مدیریت یک ارائه فراهم می‌کند. هر [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) با یک شیء `PresentationConnection` نشان داده می‌شود. هم [عامل کاربر کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) و هم [عامل کاربر دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-user-agent) _باید_ `PresentationConnection` را پیاده‌سازی کنند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PresentationConnection.binaryType")}} {{Experimental_Inline}}
  - : مقدار `blob` یا `arrayBuffer` را برمی‌گرداند. وقتی یک شیء `PresentationConnection` ساخته می‌شود، ویژگی IDL مربوط به [`binaryType`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection-binarytype) آن، _باید_ روی رشته [`"arraybuffer"`](https://www.w3.org/TR/presentation-api/#dom-binarytype-arraybuffer) تنظیم شود.
- {{domxref("PresentationConnection.id")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شناسه اتصال ارائه را فراهم می‌کند.
- {{domxref("PresentationConnection.state")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : وضعیت فعلی [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) را برمی‌گرداند.
- {{domxref("PresentationConnection.url")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نشانی اینترنتی (URL) مورد استفاده برای ایجاد یا اتصال مجدد به ارائه را برمی‌گرداند.

## متدهای نمونه

- {{domxref("PresentationConnection.close()")}} {{Experimental_Inline}}
  - : اتصال فعلی را می‌بندد و یک رویداد {{domxref("PresentationConnectionCloseEvent")}} را برای رویداد {{DOMxRef("PresentationConnection/close", "close")}} ارسال می‌کند.
- {{domxref("PresentationConnection.send()")}} {{Experimental_Inline}}
  - : داده‌های متنی یا دودویی را بین یک زمینه مرور کنترل‌کننده و یک زمینه مرور ارائه‌دهنده ارسال می‌کند.
- {{domxref("PresentationConnection.terminate()")}} {{Experimental_Inline}}
  - : اتصال فعلی را خاتمه می‌دهد و رویداد {{domxref("PresentationConnection/terminate_event", "terminate")}} را صادر می‌کند.

## رویدادها

- {{domxref("PresentationConnection/close_event", "close")}} {{Experimental_Inline}}
  - : هنگام فراخوانی {{DOMxRef("PresentationConnection.close", "PresentationConnection.close()")}} صادر می‌شود.
- {{domxref("PresentationConnection/connect_event", "connect")}} {{Experimental_Inline}}
  - : وقتی یک اتصال ارائه برقرار می‌شود صادر می‌گردد.
- {{domxref("PresentationConnection/message_event", "message")}} {{Experimental_Inline}}
  - : هنگام فراخوانی {{DOMxRef("PresentationConnection.send", "PresentationConnection.send()")}} صادر می‌شود.
- {{domxref("PresentationConnection/terminate_event", "terminate")}} {{Experimental_Inline}}
  - : هنگام فراخوانی {{DOMxRef("PresentationConnection.terminate", "PresentationConnection.terminate()")}} صادر می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}