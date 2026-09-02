---
title: "HTMLTemplateElement: shadowRootSlotAssignment property"
---

---
title: "HTMLTemplateElement: shadowRootSlotAssignment property"
short-title: shadowRootSlotAssignment
slug: Web/API/HTMLTemplateElement/shadowRootSlotAssignment
page-type: web-api-instance-property
browser-compat: api.HTMLTemplateElement.shadowRootSlotAssignment
---

{{APIRef("Web Components")}}

ویژگی **`shadowRootSlotAssignment`** در رابط {{domxref("HTMLTemplateElement")}} مشخص می‌کند که آیا عنصر برای استفاده از [اختصاص اسلات نامدار یا بدون نام](/en-US/docs/Web/API/Web_components/Using_templates_and_slots#named_and_manual_slot_assignment) پیکربندی شده است.

از این ویژگی می‌توان برای [تشخیص پشتیبانی از ویژگی اعلانی (declarative attribute)](#feature_detection_for_shadowrootslotassignment) روی عنصر {{htmlelement("template")}} استفاده کرد.

نمی‌توان این ویژگی را برای تعیین روش اختصاص اسلات یک shadow root خواند.
دلیل این است که اعلان یک عنصر `<template>` منجر به ایجاد یک `HTMLTemplateElement` یا یک `ShadowRoot` می‌شود.
اگر یک shadow root ایجاد شود، `HTMLTemplateElement` ایجاد نمی‌شود؛ بنابراین نمی‌توانید از آن برای بررسی اختصاص اسلات استفاده کنید.
اگر یک `HTMLTemplateElement` ایجاد شود، آنگاه یک shadow root نیست و به‌سادگی نیز نمی‌توان آن را به یکی تبدیل کرد — بنابراین مقدار آن بی‌اهمیت است.

اگر تعریف شده باشد، این ویژگی مقدار ویژگی [`shadowrootslotassignment`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootslotassignment) عنصر {{htmlelement("template")}} مرتبط را بازتاب می‌دهد.

## مقدار

یک رشته (string) که مقدار ویژگی [`shadowrootslotassignment`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootslotassignment) عنصر [`<template>`](/en-US/docs/Web/HTML/Reference/Elements/template) مرتبط را بازتاب می‌دهد.
مقادیر ممکن `"named"` و `"manual"` هستند.

## مثال‌ها

### تشخیص پشتیبانی برای `shadowrootslotassignment`

اگر با استفاده از عناصر {{htmlelement("template")}} به‌صورت اعلانی shadow rootهایی می‌سازید که به اختصاص اسلات بدون نام متکی هستند، می‌توانید از وجود این ویژگی روی `HTMLTemplateElement` برای بررسی پشتیبانی (feature check) استفاده کنید.
این روش کار می‌کند، زیرا این ویژگی همزمان با اختصاص بدون نام با استفاده از مقدار `"manual"` اضافه شده است.

```js
const isShadowRootSlotAssignmentSupported = Object.hasOwn(
  HTMLTemplateElement.prototype,
  "shadowRootSlotAssignment",
);
```

سپس می‌توان از مقدار `isShadowRootSlotAssignmentSupported` برای بازگشت به روش جایگزین (fallback) استفاده کرد؛ یعنی اتصال shadow root با {{domxref("Element.attachShadow()")}}، یا به کاربر اطلاع داد که باید از چه نسخه‌هایی از مرورگر استفاده کند.

توجه داشته باشید که اگر از اختصاص اسلات نامدار استفاده می‌کنید، نیازی به بررسی پشتیبانی برای `shadowrootslotassignment` نیست، زیرا اختصاص نامدار به‌صورت پیش‌فرض پشتیبانی می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`shadowrootslotassignment`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootslotassignment) عنصر `<template>`
- [`ShadowRoot.slotAssignment`](/en-US/docs/Web/API/ShadowRoot/slotAssignment)