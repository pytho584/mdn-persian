---
title: "MediaKeyStatusMap"
slug: Web/API/MediaKeyStatusMap
page-type: web-api-interface
browser-compat: api.MediaKeyStatusMap
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

رابط **`MediaKeyStatusMap`** از [API افزونه‌های رسانه رمزگذاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) یک نقشه فقط‌خواندنی از وضعیت‌های کلید رسانه بر اساس شناسه‌های کلید است.

## ویژگی‌های نمونه

- {{domxref("MediaKeyStatusMap.size")}} {{ReadOnlyInline}}
  - : تعداد جفت‌های کلید/مقدار در نقشه وضعیت را برمی‌گرداند.

## روش‌های نمونه

- {{domxref("MediaKeyStatusMap.entries()")}} {{ReadOnlyInline}}
  - : یک شیء `Iterator` جدید برمی‌گرداند که شامل آرایه‌ای از `[key, value]` برای هر عنصر در نقشه وضعیت، به ترتیب درج است.
- {{domxref("MediaKeyStatusMap.forEach()")}} {{ReadOnlyInline}}
  - : یک بار برای هر جفت کلید-مقدار در نقشه وضعیت، به ترتیب درج، `callback` را فراخوانی می‌کند. اگر `argument` وجود داشته باشد، به تابع callback ارسال می‌شود.
- {{domxref("MediaKeyStatusMap.get()")}} {{ReadOnlyInline}}
  - : مقدار مرتبط با کلید داده شده را برمی‌گرداند، یا اگر وجود نداشته باشد `undefined` را برمی‌گرداند.
- {{domxref("MediaKeyStatusMap.has()")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا مقداری با کلید داده شده مرتبط شده است یا خیر.
- {{domxref("MediaKeyStatusMap.keys()")}} {{ReadOnlyInline}}
  - : یک شیء `Iterator` جدید برمی‌گرداند که شامل کلیدهای هر عنصر در نقشه وضعیت، به ترتیب درج است.
- {{domxref("MediaKeyStatusMap.values()")}} {{ReadOnlyInline}}
  - : یک شیء `Iterator` جدید برمی‌گرداند که شامل مقادیر هر عنصر در نقشه وضعیت، به ترتیب درج است.
- `MediaKeyStatusMap[Symbol.iterator]()` {{ReadOnlyInline}}
  - : یک شیء `Iterator` جدید برمی‌گرداند که شامل آرایه‌ای از `[key, value]` برای هر عنصر در نقشه وضعیت، به ترتیب درج است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}