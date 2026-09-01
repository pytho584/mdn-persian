```
---
title: "EditContext"
---

---
title: EditContext
slug: Web/API/EditContext
page-type: web-api-interface
status:
  - experimental
browser-compat: api.EditContext
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

رابط **`EditContext`** زمینهٔ ویرایش متن عنصری را نشان می‌دهد که با استفاده از {{domxref("EditContext API", "", "", "nocode")}} قابل ویرایش شده است.

از {{domxref("EditContext API", "", "", "nocode")}} می‌توان برای ساخت ویرایشگرهای متنی پیشرفته در وب استفاده کرد که تجربه‌های ورود متن پیچیده‌تری مانند ترکیب متن با {{glossary("Input Method Editor")}} (IME)، انتخاب‌گر ایموجی، یا هر رابط کاربری ویرایش وابسته به پلتفرم دیگری را پشتیبانی می‌کنند.

## سازنده

- {{domxref("EditContext.EditContext", "EditContext()")}} {{experimental_inline}}
  - : یک نمونه جدید `EditContext` برمی‌گرداند.

## ویژگی‌های نمونه

- {{domxref("EditContext.text")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : محتوای قابل ویرایش عنصر.
- {{domxref("EditContext.selectionStart")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : آفست شروع انتخاب فعلی در محتوای متن قابل ویرایش.
- {{domxref("EditContext.selectionEnd")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : آفست پایان انتخاب فعلی در محتوای متن قابل ویرایش.
- {{domxref("EditContext.characterBoundsRangeStart")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : آفست محل شروع آخرین ترکیب IME در محتوای متن قابل ویرایش.

## روش‌های نمونه

_`EditContext` بر پایهٔ رابط {{domxref("EventTarget")}} است و روش‌های آن را نیز شامل می‌شود._

- {{domxref("EditContext.attachedElements()")}} {{experimental_inline}}
  - : یک {{jsxref("Array")}} شامل یک شیء {{domxref("HTMLElement")}} که عنصر مرتبط با شیء `EditContext` است.
- {{domxref("EditContext.characterBounds()")}} {{experimental_inline}}
  - : فهرست مستطیل‌های محدودکننده برای کاراکترهای موجود در شیء `EditContext`.
- {{domxref("EditContext.updateText()")}} {{experimental_inline}}
  - : محتوای متنی داخلی شیء `EditContext` را به‌روزرسانی می‌کند.
- {{domxref("EditContext.updateSelection()")}} {{experimental_inline}}
  - : وضعیت داخلی انتخاب را در زمینهٔ متن قابل ویرایش به‌روزرسانی می‌کند.
- {{domxref("EditContext.updateControlBounds()")}} {{experimental_inline}}
  - : موقعیت و اندازهٔ ناحیهٔ متن قابل ویرایش را به سیستم‌عامل اطلاع می‌دهد.
- {{domxref("EditContext.updateSelectionBounds()")}} {{experimental_inline}}
  - : موقعیت و اندازهٔ انتخاب در ناحیهٔ متن قابل ویرایش را به سیستم‌عامل اطلاع می‌دهد.
- {{domxref("EditContext.updateCharacterBounds()")}} {{experimental_inline}}
  - : موقعیت و اندازهٔ کاراکترهای موجود در شیء `EditContext` را به سیستم‌عامل اطلاع می‌دهد.

## رویدادها

- {{domxref("EditContext.textupdate_event", "textupdate")}} {{experimental_inline}}
  - : هنگامی که کاربر تغییراتی در متن یا انتخاب ایجاد کرده است، فعال می‌شود.
- {{domxref("EditContext.textformatupdate_event", "textformatupdate")}} {{experimental_inline}}
  - : زمانی که ترکیب متن با استفاده از پنجرهٔ {{glossary("Input Method Editor")}} (IME) در حال انجام است و IME تصمیم می‌گیرد بخش‌هایی از متن در حال ترکیب برای نشان‌دادن وضعیت ترکیب، قالب‌بندی متفاوتی داشته باشند، فعال می‌شود.
- {{domxref("EditContext.characterboundsupdate_event", "characterboundsupdate")}} {{experimental_inline}}
  - : زمانی که سیستم‌عامل برای نمایش پنجرهٔ IME نیاز به دانستن اندازه و موقعیت برخی کاراکترها در ناحیهٔ متن قابل ویرایش شیء `EditContext` دارد، فعال می‌شود.
- {{domxref("EditContext.compositionstart_event", "compositionstart")}} {{experimental_inline}}
  - : هنگامی که ترکیب متن با استفاده از پنجرهٔ IME شروع می‌شود، فعال می‌شود.
- {{domxref("EditContext.compositionend_event", "compositionend")}} {{experimental_inline}}
  - : هنگامی که ترکیب متن با استفاده از پنجرهٔ IME پایان می‌یابد، فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```