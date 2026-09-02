---
title: MediaRecorderErrorEvent
slug: Web/API/MediaRecorderErrorEvent
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.MediaRecorderErrorEvent
---

{{APIRef("MediaStream Recording")}}{{Deprecated_Header}}{{Non-standard_Header}}

اینترفیس **`MediaRecorderErrorEvent`** خطاهای بازگشت‌داده‌شده توسط [MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API) را نمایش می‌دهد. این یک شیء {{domxref("Event")}} است که یک ارجاع به {{domxref("DOMException")}} را در خود جای می‌دهد و خطای رخ‌داده را توصیف می‌کند.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("MediaRecorderErrorEvent.MediaRecorderErrorEvent", "MediaStreamRecorderEvent()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک شیء رویداد جدید از نوع `MediaRecorderErrorEvent` با پارامترهای داده‌شده ایجاد و بازمی‌گرداند.

## ویژگی‌های نمونه (Instance properties)

_ویژگی‌ها را از اینترفیس والد خود، یعنی {{domxref("Event")}} به ارث می‌برد._

- {{domxref("MediaRecorderErrorEvent.error", "error")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک {{domxref("DOMException")}} که شامل اطلاعاتی دربارهٔ خطای رخ‌داده است.

## روش‌های نمونه (Instance methods)

_روش‌ها را از اینترفیس والد خود، یعنی {{domxref("Event")}} به ارث می‌برد._

## مشخصات (Specifications)

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگرها (Browser compatibility)

{{Compat}}