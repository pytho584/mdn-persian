---
title: DOMRectList
slug: Web/API/DOMRectList
page-type: web-api-interface
browser-compat: api.DOMRectList
---

{{APIRef("Geometry Interfaces")}}

رابط **`DOMRectList`** مجموعه‌ای از اشیاء {{domxref("DOMRect")}} را نشان می‌دهد و معمولاً برای نگهداری مستطیل‌های مرتبط با یک عنصر خاص استفاده می‌شود؛ مانند جعبه‌های محدودکننده (bounding boxes) که توسط روش‌هایی مثل {{domxref("Element.getClientRects", "getClientRects()")}} بازگردانده می‌شوند. این رابط از طریق ایندکس، دسترسی به هر مستطیل در فهرست را فراهم می‌کند و همراه با آن، ویژگی `length` تعداد کل مستطیل‌ها را در فهرست نشان می‌دهد.

> [!NOTE]
> `DOMRectList` برای سازگاری با محتوای قدیمی وب وجود دارد و هنگام ایجاد APIهای جدید استفاده از آن توصیه نمی‌شود.

## ویژگی‌های نمونه

- {{domxref("DOMRectList.length")}} {{ReadOnlyInline}}
  - : ویژگی فقط‌خواندنی که تعداد کل اشیاء {{domxref("DOMRect")}} را در `DOMRectList` برمی‌گرداند.

## روش‌های نمونه

- {{domxref("DOMRectList.item")}}
  - : شیء {{domxref("DOMRect")}} را در ایندکس مشخص‌شده برمی‌گرداند. اگر `index` خارج از محدوده باشد، مقدار `null` بازگردانده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMRect")}}
- {{domxref("DOMRectReadOnly")}}