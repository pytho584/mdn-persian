---
title: "HTMLTemplateElement: shadowRootCustomElementRegistry property"
short-title: shadowRootCustomElementRegistry
slug: Web/API/HTMLTemplateElement/shadowRootCustomElementRegistry
page-type: web-api-instance-property
browser-compat: api.HTMLTemplateElement.shadowRootCustomElementRegistry
---

{{APIRef("Web Components")}}

ویژگی **`shadowRootCustomElementRegistry`** از رابط {{domxref("HTMLTemplateElement")}}، مقدار ویژگی `shadowrootcustomelementregistry` عنصر [`<template>`](/en-US/docs/Web/HTML/Reference/Elements/template) مرتبط را منعکس می‌کند.

> [!NOTE] این ویژگی برای توسعه‌دهندگان مفید نیست و تنها برای کامل بودن مستند شده است. اگر یک عنصر `<template>` برای ایجاد اعلامی یک [`ShadowRoot`](/en-US/docs/Web/API/ShadowRoot) استفاده شود، این شیء و ویژگی وجود ندارند. در غیر این صورت، اگر یک `HTMLTemplateElement` ایجاد شود، مقدار این ویژگی بی‌ربط است زیرا شیء یک ریشه سایه نیست و نمی‌تواند بعداً به یک ریشه سایه تبدیل شود.

## مقدار

یک رشته که ویژگی `shadowrootcustomelementregistry` عنصر [`<template>`](/en-US/docs/Web/HTML/Reference/Elements/template) مرتبط را منعکس می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ShadowRoot.customElementRegistry")}}
- {{domxref("HTMLTemplateElement.shadowRootMode")}}
- سازنده {{domxref("CustomElementRegistry.CustomElementRegistry()", "CustomElementRegistry()")}}
- [استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements)