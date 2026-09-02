---
title: "MediaEncryptedEvent"
---

---
title: MediaEncryptedEvent
slug: Web/API/MediaEncryptedEvent
page-type: web-api-interface
browser-compat: api.MediaEncryptedEvent
---

{{APIRef("Encrypted Media Extensions")}}

رابط **`MediaEncryptedEvent`** از [API اکستنشن‌های رسانه‌های رمزنگاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) اطلاعات مرتبط با رویداد {{domxref("HTMLMediaElement/encrypted_event", "encrypted")}} را که به یک {{domxref("HTMLMediaElement")}} ارسال می‌شود، زمانی که داده‌های اولیه‌ای در رسانه یافت می‌شود، در بر می‌گیرد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MediaEncryptedEvent.MediaEncryptedEvent", "MediaEncryptedEvent()")}}
  - : یک نمونه جدید از شیء `MediaEncryptedEvent` می‌سازد.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

- {{domxref("MediaEncryptedEvent.initDataType")}} {{ReadOnlyInline}}
  - : یک رشته حساس به حروف بزرگ و کوچک (case-sensitive) شامل _نوع_ قالب داده‌های اولیه یافت‌شده را برمی‌گرداند.
- {{domxref("MediaEncryptedEvent.initData")}} {{ReadOnlyInline}}
  - : یک {{jsxref("ArrayBuffer")}} حاوی داده‌های اولیه یافت‌شده را برمی‌گرداند. اگر هیچ داده اولیه‌ای مرتبط با قالب وجود نداشته باشد، `null` برمی‌گرداند.

## روش‌های نمونه

_این رابط هیچ روش خاصی ارائه نمی‌دهد، اما روش‌ها را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}