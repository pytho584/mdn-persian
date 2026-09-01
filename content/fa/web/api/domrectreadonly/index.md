---
title: "DOMRectReadOnly"
---

---
title: DOMRectReadOnly
slug: Web/API/DOMRectReadOnly
page-type: web-api-interface
browser-compat: api.DOMRectReadOnly
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

اینترفیس **`DOMRectReadOnly`** ویژگی‌های استانداردی را مشخص می‌کند (که توسط {{domxref("DOMRect")}} نیز استفاده می‌شود) برای تعریف یک مستطیل که ویژگی‌های آن تغییرناپذیر هستند.

## سازنده

- {{domxref("DOMRectReadOnly.DOMRectReadOnly","DOMRectReadOnly()")}}
  - : برای ایجاد یک شیء جدید `DOMRectReadOnly` تعریف شده است.

## ویژگی‌های نمونه

- {{domxref("DOMRectReadOnly.x")}} {{ReadOnlyInline}}
  - : مختصات x مبدأ `DOMRectReadOnly` را برمی‌گرداند.
- {{domxref("DOMRectReadOnly.y")}} {{ReadOnlyInline}}
  - : مختصات y مبدأ `DOMRectReadOnly` را برمی‌گرداند.
- {{domxref("DOMRectReadOnly.width")}} {{ReadOnlyInline}}
  - : عرض `DOMRectReadOnly` را برمی‌گرداند.
- {{domxref("DOMRectReadOnly.height")}} {{ReadOnlyInline}}
  - : ارتفاع `DOMRectReadOnly` را برمی‌گرداند.
- {{domxref("DOMRectReadOnly.top")}} {{ReadOnlyInline}}
  - : مقدار مختصات بالای `DOMRectReadOnly` را برمی‌گرداند (معمولاً همان `y` است).
- {{domxref("DOMRectReadOnly.right")}} {{ReadOnlyInline}}
  - : مقدار مختصات راست `DOMRectReadOnly` را برمی‌گرداند (معمولاً همان `x + width` است).
- {{domxref("DOMRectReadOnly.bottom")}} {{ReadOnlyInline}}
  - : مقدار مختصات پایین `DOMRectReadOnly` را برمی‌گرداند (معمولاً همان `y + height` است).
- {{domxref("DOMRectReadOnly.left")}} {{ReadOnlyInline}}
  - : مقدار مختصات چپ `DOMRectReadOnly` را برمی‌گرداند (معمولاً همان `x` است).

## روش‌های ایستا

- {{domxref("DOMRectReadOnly/fromRect_static", "DOMRectReadOnly.fromRect()")}}
  - : یک شیء جدید `DOMRectReadOnly` با موقعیت و ابعاد مشخص ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("DOMRectReadOnly.toJSON()")}}
  - : یک نمایش JSON از شیء `DOMRectReadOnly` برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPoint")}}