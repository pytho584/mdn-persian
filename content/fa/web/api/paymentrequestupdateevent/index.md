---
title: PaymentRequestUpdateEvent
slug: Web/API/PaymentRequestUpdateEvent
page-type: web-api-interface
browser-compat: api.PaymentRequestUpdateEvent
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

رابطهٔ **`PaymentRequestUpdateEvent`** برای رویدادهایی استفاده می‌شود که وقتی تغییراتی در اطلاعات مربوط به حمل‌ونقل برای یک {{domxref("PaymentRequest")}} در انتظار ایجاد می‌شود، به یک نمونه ارسال می‌گردند. این رویدادها عبارت‌اند از:

- {{domxref("PaymentRequest.shippingaddresschange_event", "shippingaddresschange")}}
  - : هر زمان که کاربر آدرس حمل‌ونقل خود را تغییر دهد، این رویداد ارسال می‌شود.
- {{domxref("PaymentRequest.shippingoptionchange_event", "shippingoptionchange")}}
  - : هر زمان که کاربر یک گزینهٔ حمل‌ونقل را تغییر دهد، این رویداد ارسال می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PaymentRequestUpdateEvent.PaymentRequestUpdateEvent()","PaymentRequestUpdateEvent()")}}
  - : یک شیء `PaymentRequestUpdateEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_فقط ویژگی‌های به‌ارث‌برده‌شده از رابط والد، یعنی {{domxref("Event")}} را فراهم می‌کند._

## روش‌های نمونه

_علاوه بر روش‌های به‌ارث‌برده‌شده از رابط والد، یعنی {{domxref("Event")}}، `PaymentRequestUpdateEvent` روش‌های زیر را نیز ارائه می‌دهد:_

- {{domxref("PaymentRequestUpdateEvent.updateWith()")}}
  - : اگر کنترل‌کنندهٔ رویداد تشخیص دهد که اطلاعات موجود در درخواست پرداخت باید تغییر کند یا اطلاعات جدیدی باید اضافه شود، `updateWith()` را با اطلاعاتی که باید جایگزین یا اضافه شوند فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)