---
title: "EditContext: characterBounds() method"
short-title: characterBounds()
slug: Web/API/EditContext/characterBounds
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.characterBounds
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`characterBounds()`** از رابط {{domxref("EditContext")}} یک {{jsxref("Array")}} شامل لیست مستطیل‌های مرزی (bounding rectangles) برای کاراکترهای موجود در شیء `EditContext` بازمی‌گرداند.

موقعیت و اندازه کاراکترها در یک شیء `EditContext` توسط سیستم‌عامل برای تعیین موقعیت صحیح سطوح رابط کاربری ویرایشی مختص پلتفرم، مانند پنجره {{glossary("Input Method Editor")}} (ویرایشگر روش ورودی، IME) در صورت نیاز استفاده می‌شود. این موضوع به‌ویژه در شرایطی که سیستم‌عامل نمی‌تواند به‌طور خودکار موقعیت و اندازه کاراکترها را تشخیص دهد، مانند زمانی که متن در یک عنصر `<canvas>` رندر می‌شود، اهمیت دارد.

توسعه‌دهندگان وب به احتمال زیاد به استفاده از رویداد {{domxref("EditContext.characterboundsupdate_event", "characterboundsupdate")}} به همراه متد {{domxref("EditContext.updateCharacterBounds()")}} برای به‌روزرسانی مرزهای کاراکترها زمانی که سیستم‌عامل نشان می‌دهد به اطلاعاتی درباره موقعیت و اندازه کاراکترها نیاز دارد، علاقه‌مند خواهند بود.

متد `characterBounds()` لیست مرزهای کاراکترهایی را که آخرین بار با `updateCharacterBounds()` به‌روزرسانی شده‌اند، بازمی‌گرداند. این لیست شامل یک آیتم برای هر کاراکتر در شیء `EditContext` نیست، بلکه فقط برای کاراکترهایی است که با `updateCharacterBounds()` به‌روزرسانی شده‌اند. برای دانستن محل قرارگیری کاراکترها در شیء `EditContext`، از ویژگی {{domxref("EditContext.characterBoundsRangeStart")}} استفاده کنید.

## نحو

```js-nolint
characterBounds()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Array")}} شامل اشیاء {{domxref("DOMRect")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.