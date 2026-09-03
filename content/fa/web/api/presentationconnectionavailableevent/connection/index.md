---
title: "PresentationConnectionAvailableEvent: connection property"
short-title: connection
slug: Web/API/PresentationConnectionAvailableEvent/connection
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PresentationConnectionAvailableEvent.connection
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

هنگامی که یک اتصال ورودی ایجاد می‌شود، یک [عامل کاربرِ دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-user-agent) یک [رویدادِ مورد اعتماد](https://www.w3.org/TR/presentation-api/#dfn-trusted-event) به نام [`connectionavailable`](https://www.w3.org/TR/presentation-api/#dfn-connectionavailable) را روی یک [`PresentationReceiver`](https://www.w3.org/TR/presentation-api/#idl-def-presentationreceiver) [صادر می‌کند](https://www.w3.org/TR/presentation-api/#dfn-firing-an-event). این [رویدادِ مورد اعتماد](https://www.w3.org/TR/presentation-api/#dfn-trusted-event) با استفاده از واسطِ [`PresentationConnectionAvailableEvent`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionavailableevent) روی [پایشگرِ کنترل‌کنندهٔ ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-controllers-monitor) صادر می‌شود و ویژگی [`connection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionavailableevent-connection) آن برابر با شیءِ [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) که ایجاد شده است قرار می‌گیرد.

این رویداد برای همهٔ اتصال‌هایی صادر می‌شود که هنگام [پایش اتصال‌های ورودیِ ارائه](https://www.w3.org/TR/presentation-api/#dfn-monitoring-incoming-presentation-connections) ایجاد می‌شوند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}