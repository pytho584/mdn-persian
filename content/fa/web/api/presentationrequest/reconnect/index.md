---
title: "PresentationRequest: reconnect() method"
short-title: reconnect()
slug: Web/API/PresentationRequest/reconnect
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PresentationRequest.reconnect
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

هنگامی که متد `reconnect(presentationId)` روی یک `PresentationRequest` _presentationRequest_ فراخوانی می‌شود، [عامل کاربر](https://www.w3.org/TR/presentation-api/#dfn-user-agents) _باید_ مراحل زیر را برای _اتصال مجدد به یک ارائه_ اجرا کند:

## ورودی

- _presentationRequest_، شیء [`PresentationRequest`](https://www.w3.org/TR/presentation-api/#idl-def-presentationrequest) که [`reconnect()`](https://www.w3.org/TR/presentation-api/#dom-presentationrequest-reconnect) روی آن فراخوانی شده است.
- _presentationId_، یک [شناسه ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-identifier) معتبر

## خروجی

_P_، یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise).

## الگوریتم

1. با استفاده از [شیء تنظیمات](https://www.w3.org/TR/presentation-api/#dfn-settings-object) سند، [الگوریتم ممنوعیت زمینه‌های امنیتی ترکیبی](https://www.w3.org/TR/presentation-api/#dfn-prohibits-mixed-security-contexts-algorithm) را اجرا کنید.
2. اگر نتیجه الگوریتم `"Prohibits Mixed Security Contexts"` باشد و [URL درخواست ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-request-urls) _presentationRequest_ یک [URL از پیش تأییدنشده](https://www.w3.org/TR/presentation-api/#dfn-a-priori-unauthenticated-url) باشد، یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise) برگردانید که با یک [`SecurityError`](https://www.w3.org/TR/presentation-api/#dfn-securityerror) رد شده است و این مراحل را متوقف کنید.
3. اگر [مجموعه پرچم‌های sandboxing فعال](https://www.w3.org/TR/presentation-api/#dfn-active-sandboxing-flag-set) شیء سند دارای [پرچم زمینه مرور ارائه sandboxed](https://www.w3.org/TR/presentation-api/#sandboxed-presentation-browsing-context-flag) است، یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise) برگردانید که با یک [`SecurityError`](https://www.w3.org/TR/presentation-api/#dfn-securityerror) رد شده است و این مراحل را متوقف کنید.
4. اجازه دهید _P_ یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise) جدید باشد.
5. _P_ را برگردانید اما اجرای این مراحل را به صورت موازی ادامه دهید.
6. [مجموعه ارائه‌های تحت کنترل](https://www.w3.org/TR/presentation-api/#dfn-set-of-controlled-presentations) را برای یک [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) جستجو کنید که معیارهای زیر را داشته باشد: [زمینه مرور کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-browsing-context) آن، [زمینه مرور](https://www.w3.org/TR/presentation-api/#dfn-browsing-context) فعلی است، [وضعیت اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection-state) آن [`terminated`](https://www.w3.org/TR/presentation-api/#dom-presentationconnectionstate-terminated) نیست، [URL ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-url) آن برابر با یکی از [URLهای درخواست ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-request-urls) _presentationRequest_ است و [شناسه ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-identifier) آن برابر با _presentationId_ است.
7. اگر چنین [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) وجود دارد، مراحل زیر را اجرا کنید:
   1. اجازه دهید _S_ آن [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) باشد.
   2. _P_ را با _S_ [resolve](https://www.w3.org/TR/presentation-api/#dfn-resolving-a-promise) کنید.
   3. اگر [وضعیت اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection-state) _S_ [`connecting`](https://www.w3.org/TR/presentation-api/#dom-presentationconnectionstate-connecting) یا [`connected`](https://www.w3.org/TR/presentation-api/#dom-presentationconnectionstate-connected) است، تمام مراحل باقی‌مانده را متوقف کنید.
   4. [وضعیت اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection-state) _S_ را به [`connecting`](https://www.w3.org/TR/presentation-api/#dom-presentationconnectionstate-connecting) تنظیم کنید.
   5. یک [اتصال ارائه برقرار کنید](https://www.w3.org/TR/presentation-api/#dfn-establish-a-presentation-connection) با _S_.
   6. تمام مراحل باقی‌مانده را متوقف کنید.

8. [مجموعه ارائه‌های تحت کنترل](https://www.w3.org/TR/presentation-api/#dfn-set-of-controlled-presentations) را برای اولین [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) جستجو کنید که معیارهای زیر را داشته باشد: [وضعیت اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection-state) آن [`terminated`](https://www.w3.org/TR/presentation-api/#dom-presentationconnectionstate-terminated) نیست، [URL ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-url) آن برابر با یکی از [URLهای درخواست ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-request-urls) _presentationRequest_ است و [شناسه ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-identifier) آن برابر با _presentationId_ است.
9. اگر چنین [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) وجود دارد، اجازه دهید _E_ آن [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) باشد و مراحل زیر را اجرا کنید:
   1. یک [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) جدید به نام _S_ ایجاد کنید.
   2. [شناسه ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-identifier) _S_ را به _presentationId_ تنظیم کنید.
   3. [URL ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-url) _S_ را به [URL ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-url) _E_ تنظیم کنید.
   4. [وضعیت اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection-state) _S_ را به [`connecting`](https://www.w3.org/TR/presentation-api/#dom-presentationconnectionstate-connecting) تنظیم کنید.
   5. _S_ را به [مجموعه ارائه‌های تحت کنترل](https://www.w3.org/TR/presentation-api/#dfn-set-of-controlled-presentations) اضافه کنید.
   6. _P_ را با _S_ [resolve](https://www.w3.org/TR/presentation-api/#dfn-resolving-a-promise) کنید.
   7. یک [کار](https://www.w3.org/TR/presentation-api/#dfn-queue-a-task) را در صف قرار دهید تا یک [رویداد مورد اعتماد](https://www.w3.org/TR/presentation-api/#dfn-trusted-event) با نام [`connectionavailable`](https://www.w3.org/TR/presentation-api/#dfn-connectionavailable) که از رابط [`PresentationConnectionAvailableEvent`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionavailableevent) با ویژگی [`connection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionavailableevent-connection) مقداردهی‌شده به _S_ استفاده می‌کند، در _presentationRequest_ [fire](https://www.w3.org/TR/presentation-api/#dfn-firing-an-event) کند. رویداد نباید حباب بزند و قابل لغو باشد و نباید هیچ action پیش‌فرضی داشته باشد.
   8. یک [اتصال ارائه برقرار کنید](https://www.w3.org/TR/presentation-api/#dfn-establish-a-presentation-connection) با _S_.
   9. تمام مراحل باقی‌مانده را متوقف کنید.

10. _P_ را با یک استثنا [`NotFoundError`](https://www.w3.org/TR/presentation-api/#dfn-notfounderror) [reject](https://www.w3.org/TR/presentation-api/#dfn-rejecting-a-promise) کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}