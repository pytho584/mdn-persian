---
title: MediaKeySession
slug: Web/API/MediaKeySession
page-type: web-api-interface
browser-compat: api.MediaKeySession
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

**`MediaKeySession`** رابط [API افزونه‌های رسانه رمزنگاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) است که زمینه‌ای برای تبادل پیام با ماژول رمزگشایی محتوا (CDM) فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("MediaKeySession.closed")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که هنگام بسته‌شدن `MediaKeySession` علامت می‌دهد. این قول فقط می‌تواند fulfilled شود و هرگز rejected نمی‌شود. بستن یک نشست به این معنی است که مجوزها و کلیدهای مرتبط با آن دیگر برای رمزگشایی داده‌های رسانه معتبر نیستند.
- {{domxref("MediaKeySession.expiration")}} {{ReadOnlyInline}}
  - : زمانی که پس از آن دیگر نمی‌توان از کلیدهای نشست فعلی برای رمزگشایی داده‌های رسانه استفاده کرد، یا `NaN` اگر چنین زمانی وجود نداشته باشد. این مقدار توسط CDM تعیین می‌شود و بر حسب میلی‌ثانیه از ۱ ژانویه ۱۹۷۰ UTC اندازه‌گیری می‌شود. این مقدار ممکن است در طول عمر نشست تغییر کند، مثلاً وقتی عملی باعث شروع یک بازه زمانی می‌شود.
- {{domxref("MediaKeySession.keyStatuses")}} {{ReadOnlyInline}}
  - : ارجاعی به یک {{domxref("MediaKeyStatusMap")}} فقط‌خواندنی از کلیدهای نشست فعلی و وضعیت‌های آن‌ها را نگه می‌دارد.
- {{domxref("MediaKeySession.sessionId")}} {{ReadOnlyInline}}
  - : یک رشته یکتا که توسط CDM برای شیء رسانه فعلی و کلیدها یا مجوزهای مرتبط با آن تولید شده است را نگه می‌دارد.

### رویدادها

- {{domxref("MediaKeySession.keystatuseschange_event", "keystatuseschange")}}
  - : وقتی تغییری در کلیدهای یک نشست یا وضعیت‌های آن‌ها رخ می‌دهد، فعال می‌شود.
- {{domxref("MediaKeySession.message_event", "message")}}
  - : وقتی ماژول رمزگشایی محتوا پیامی برای نشست تولید کرده است، فعال می‌شود.

## روش‌های نمونه

- {{domxref("MediaKeySession.close()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند پس از اینکه اعلام می‌کند نشست رسانه فعلی دیگر مورد نیاز نیست و CDM باید هر منبع مرتبط با این شیء را آزاد کرده و آن را ببندد.
- {{domxref("MediaKeySession.generateRequest()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند پس از تولید درخواست مجوز بر اساس داده‌های مقداردهی اولیه.
- {{domxref("MediaKeySession.load()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به یک مقدار بولی resolve می‌شود پس از بارگذاری داده‌ها برای یک شیء نشست مشخص.
- {{domxref("MediaKeySession.remove()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند پس از حذف هرگونه داده نشست مرتبط با شیء فعلی.
- {{domxref("MediaKeySession.update()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند پس از بارگذاری پیام‌ها و مجوزها در CDM.

## مثال‌ها

```js
// TBD
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
