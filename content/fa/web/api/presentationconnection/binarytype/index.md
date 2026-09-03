---
title: "PresentationConnection: binaryType property"
---

---
title: "PresentationConnection: binaryType property"
short-title: binaryType
slug: Web/API/PresentationConnection/binaryType
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PresentationConnection.binaryType
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

هنگامی که یک شیء {{DOMxRef("PresentationConnection")}} ایجاد میشود، خصوصیت IDL آن با نام `binaryType` _باید_ روی رشته `"arraybuffer"` تنظیم شود. هنگام خواندن، خصوصیت _باید_ آخرین مقدار خود (مقداری که در آخرین بار تنظیم شده) را بازگرداند. هنگام تنظیم، عامل کاربر _باید_ خصوصیت IDL را روی مقدار جدید تنظیم کند.

> [!NOTE]
> خصوصیت `binaryType` به توسعه‌دهندگان امکان می‌دهد نحوه در دسترس قرار گرفتن داده‌های باینری برای اسکریپت‌ها را کنترل کنند. با تنظیم این خصوصیت روی `"blob"`، داده‌های باینری به صورت `Blob` بازگردانده می‌شوند؛ با تنظیم آن روی `"arraybuffer"`، این داده‌ها به صورت {{JSxRef("ArrayBuffer")}} بازگردانده می‌شوند. مقدار پیش‌فرض این خصوصیت `"arraybuffer"` است. این خصوصیت هیچ تأثیری بر داده‌هایی که به صورت رشته ارسال می‌شوند ندارد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}