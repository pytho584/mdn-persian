---
title: PresentationRequest
slug: Web/API/PresentationRequest
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PresentationRequest
---

{{SeeCompatTable}}{{securecontext_header}}{{APIRef("Presentation API")}}

از شیء `PresentationRequest` برای شروع یا اتصال مجدد به یک ارائه استفاده میشود که توسط یک [بافتِ مرورِ کنترلکننده (controlling browsing context)](https://www.w3.org/TR/presentation-api/#dfn-controlling-browsing-context) ایجاد شده است. شیء `PresentationRequest` _الزاماً باید_ در یک [بافتِ مرورِ کنترلکننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-browsing-context) که توسط یک [عامل کاربرِ کنترلکننده (controlling user agent)](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) فراهم شده است، پیادهسازی شود.

هنگامی که یک `PresentationRequest` ساخته میشود، `urls` دادهشده _الزاماً باید_ بهعنوان فهرست _نشانیهای درخواست ارائه (presentation request URLs)_ استفاده شوند؛ بهگونهای که هر یک از آنها میتواند یک [نشانی ارائه (presentation URL)](https://www.w3.org/TR/presentation-api/#dfn-presentation-url) ممکن برای نمونهٔ `PresentationRequest` باشد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PresentationRequest.PresentationRequest","PresentationRequest()")}} {{Experimental_Inline}}
  - : یک `PresentationRequest` میسازد.

## ویژگیهای نمونه

هیچ ویژگی نمونهای ندارد.

## روشهای نمونه

- {{domxref("PresentationRequest.start()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمیگرداند که پس از آنکه عامل کاربر از کاربر میخواهد یک نمایشگر انتخاب کند و اجازهٔ استفاده از آن نمایشگر را بدهد، با یک {{DOMxRef("PresentationConnection")}} resolve میشود.
- {{domxref("PresentationRequest.reconnect()")}} {{Experimental_Inline}}
  - : وقتی متد `reconnect(presentationId)` روی یک `PresentationRequest` بهنام _presentationRequest_ فراخوانده شود، [عامل کاربر](https://www.w3.org/TR/presentation-api/#dfn-user-agents) _الزاماً باید_ مراحل زیر را برای _اتصال مجدد به یک ارائه_ اجرا کند.
- {{domxref("PresentationRequest.getAvailability()")}} {{Experimental_Inline}}
  - : وقتی متد `getAvailability()` فراخوانده شود، عامل کاربر _الزاماً باید_ مراحل را همانگونه که در پیوند آمده است اجرا کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}