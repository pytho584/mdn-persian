---
title: PresentationConnectionAvailableEvent
slug: Web/API/PresentationConnectionAvailableEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PresentationConnectionAvailableEvent
---

{{SeeCompatTable}}{{securecontext_header}}{{APIRef("Presentation API")}}

اینترفیس **`PresentationConnectionAvailableEvent`** در [Presentation API](/en-US/docs/Web/API/Presentation_API) زمانی روی یک {{domxref("PresentationRequest")}} فراخوانی می‌شود که یک اتصال مرتبط با آن شیء ایجاد شده باشد.

یک [عامل کاربر کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) یک [رویداد مورد اعتماد](https://www.w3.org/TR/presentation-api/#dfn-trusted-event) به نام [`connectionavailable`](https://www.w3.org/TR/presentation-api/#dfn-connectionavailable) را روی یک [`PresentationRequest`](https://www.w3.org/TR/presentation-api/#idl-def-presentationrequest) [به‌راه می‌اندازد](https://www.w3.org/TR/presentation-api/#dfn-firing-an-event) زمانی که یک اتصال مرتبط با آن شیء ایجاد شود. این رویداد روی نمونه `PresentationRequest` با استفاده از اینترفیس [`PresentationConnectionAvailableEvent`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionavailableevent) فراخوانی می‌شود و ویژگی [`connection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionavailableevent-connection) آن روی شیء [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) ایجادشده تنظیم می‌شود. این رویداد برای هر اتصالی که برای [کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controller) ایجاد می‌شود، فراخوانی می‌شود، چه توسط خود [کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controller) با فراخوانی `start()` یا `reconnect()`، و چه توسط [عامل کاربر کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) که به نمایندگی از کنترل‌کننده از طریق [`defaultRequest`](https://www.w3.org/TR/presentation-api/#dom-presentation-defaultrequest) اتصالی ایجاد کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PresentationConnectionAvailableEvent.PresentationConnectionAvailableEvent", "PresentationConnectionAvailableEvent()")}} {{Experimental_Inline}}
  - : یک PresentationConnectionAvailableEvent جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("PresentationConnectionAvailableEvent.connection")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : ارجاعی به شیء {{domxref("PresentationConnection")}} که رویداد را فراخوانی کرده است برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}