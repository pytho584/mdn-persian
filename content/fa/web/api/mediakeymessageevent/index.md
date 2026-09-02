```yaml
---
title: "MediaKeyMessageEvent"
slug: Web/API/MediaKeyMessageEvent
page-type: web-api-interface
browser-compat: api.MediaKeyMessageEvent
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

رابط **`MediaKeyMessageEvent`** از [API افزونه‌های رسانه رمزگذاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) حاوی محتوا و داده‌های مرتبط است، زمانی که ماژول رمزگشایی محتوا یک پیام برای نشست (session) تولید می‌کند.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("MediaKeyMessageEvent.MediaKeyMessageEvent","MediaKeyMessageEvent()")}}
  - : یک نمونه جدید از `MediaKeyMessageEvent` ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

ویژگی‌های والد خود، {{domxref("Event")}} را به ارث می‌برد.

- {{domxref("MediaKeyMessageEvent.message")}} {{ReadOnlyInline}}
  - : یک {{jsxref("ArrayBuffer")}} شامل پیامی از ماژول رمزگشایی محتوا برمی‌گرداند. پیام‌ها با توجه به سیستم کلید (key system) متفاوت هستند.
- {{domxref("MediaKeyMessageEvent.messageType")}} {{ReadOnlyInline}}
  - : نوع پیام را مشخص می‌کند. می‌تواند یکی از این مقادیر باشد: `license-request`، `license-renewal`، `license-release`، یا `individualization-request`.

## روش‌های نمونه (Instance methods)

روش‌های والد خود، {{domxref("Event")}} را به ارث می‌برد.

## مثال‌ها

```js
// TBD
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```