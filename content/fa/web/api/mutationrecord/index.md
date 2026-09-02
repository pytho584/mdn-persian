---
title: MutationRecord
slug: Web/API/MutationRecord
page-type: web-api-interface
browser-compat: api.MutationRecord
---

{{APIRef("DOM")}}

رابط **`MutationRecord`** یک رابط فقط‌خواندنی است که یک تغییر منفرد در DOM را نشان می‌دهد که توسط {{domxref("MutationObserver")}} مشاهده شده است. این شیء همان عنصرِ داخل آرایه‌ای است که به تابع بازخوان (callback) یک {{domxref("MutationObserver")}} ارسال می‌شود.

## ویژگی‌های نمونه

- {{domxref("MutationRecord.addedNodes")}} {{ReadOnlyInline}}
  - : گره‌هایی که بر اثر یک تغییر اضافه شده‌اند. اگر هیچ گره‌ای اضافه نشده باشد، یک {{domxref("NodeList")}} خالی خواهد بود.
- {{domxref("MutationRecord.attributeName")}} {{ReadOnlyInline}}
  - : نام ویژگی تغییرکرده به‌صورت رشته، یا `null`.
- {{domxref("MutationRecord.attributeNamespace")}} {{ReadOnlyInline}}
  - : فضای نام ویژگی تغییرکرده به‌صورت رشته، یا `null`.
- {{domxref("MutationRecord.nextSibling")}} {{ReadOnlyInline}}
  - : همشأن بعدی گره‌های اضافه‌شده یا حذف‌شده، یا `null`.
- {{domxref("MutationRecord.oldValue")}} {{ReadOnlyInline}}
  - : مقدار آن به {{domxref("MutationRecord.type")}} بستگی دارد:
    - برای `attributes`، مقدار ویژگی تغییرکرده پیش از تغییر است.
    - برای `characterData`، داده‌های گره تغییرکرده پیش از تغییر است.
    - برای `childList`، مقدار `null` است.
- {{domxref("MutationRecord.previousSibling")}} {{ReadOnlyInline}}
  - : همشأن قبلی گره‌های اضافه‌شده یا حذف‌شده، یا `null`.
- {{domxref("MutationRecord.removedNodes")}} {{ReadOnlyInline}}
  - : گره‌هایی که بر اثر یک تغییر حذف شده‌اند. اگر هیچ گره‌ای حذف نشده باشد، یک {{domxref("NodeList")}} خالی خواهد بود.
- {{domxref("MutationRecord.target")}} {{ReadOnlyInline}}
  - : گره‌ای که تغییر روی آن اثر گذاشته است، بسته به `MutationRecord.type`:
    - برای `attributes`، عنصری است که ویژگی آن تغییر کرده است.
    - برای `characterData`، گره `CharacterData` است.
    - برای `childList`، گره‌ای است که فرزندان آن تغییر کرده‌اند.
- {{domxref("MutationRecord.type")}} {{ReadOnlyInline}}
  - : رشته‌ای که نوع تغییر را نشان می‌دهد: اگر تغییر از نوع تغییر ویژگی باشد `attributes`، اگر تغییری روی یک گره `CharacterData` باشد `characterData`، و اگر تغییری روی درخت گره‌ها باشد `childList` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}