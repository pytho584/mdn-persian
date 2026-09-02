---
title: HTMLTemplateElement
slug: Web/API/HTMLTemplateElement
page-type: web-api-interface
browser-compat: api.HTMLTemplateElement
---

{{APIRef("Web Components")}}

رابط **`HTMLTemplateElement`** امکان دسترسی به محتویات یک عنصر HTML {{HTMLElement("template")}} را فراهم می‌کند.

> [!NOTE]
> یک تجزیه‌کنندهٔ HTML هنگام تجزیهٔ یک عنصر {{HTMLElement("template")}} بسته به ویژگی‌های `<template>` می‌تواند یا یک `HTMLTemplateElement` یا یک {{domxref("ShadowRoot")}} بسازد.
> اگر یک `HTMLTemplateElement` ساخته شود، ویژگی‌های «shadow» از روی الگو بازتاب می‌شوند.
> با این حال، این ویژگی‌ها کاربردی ندارند، زیرا یک `HTMLTemplateElement` یک ریشهٔ سایه (shadow root) نیست و بعداً نمی‌توان آن را به ریشهٔ سایه تبدیل کرد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط، ویژگی‌های {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLTemplateElement.content", "content")}} {{ReadOnlyInline}}
  - : یک {{domxref("DocumentFragment")}} فقط‌خواندنی که شامل زیردرخت DOM نمایانگر محتویات الگوی عنصر {{HTMLElement("template")}} است.
- {{domxref("HTMLTemplateElement.shadowRootMode", "shadowRootMode")}}
  - : رشته‌ای که مقدار ویژگی [`shadowrootmode`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootmode) در عنصر `<template>` مرتبط را بازتاب می‌دهد.
- {{domxref("HTMLTemplateElement.shadowRootDelegatesFocus", "shadowRootDelegatesFocus")}}
  - : یک بولی که مقدار ویژگی [`shadowrootdelegatesfocus`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootdelegatesfocus) در عنصر `<template>` مرتبط را بازتاب می‌دهد.
- {{domxref("HTMLTemplateElement.shadowRootClonable", "shadowRootClonable")}}
  - : یک بولی که مقدار ویژگی [`shadowrootclonable`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootclonable) در عنصر `<template>` مرتبط را بازتاب می‌دهد.
- {{domxref("HTMLTemplateElement.shadowRootCustomElementRegistry", "shadowRootCustomElementRegistry")}}
  - : رشته‌ای که مقدار ویژگی [`shadowrootcustomelementregistry`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootcustomelementregistry) در عنصر `<template>` مرتبط را بازتاب می‌دهد و نشان می‌دهد که ریشهٔ سایهٔ اعلانی (declarative shadow root) از یک {{domxref("CustomElementRegistry")}} محدودشده (scoped) استفاده خواهد کرد.
- {{domxref("HTMLTemplateElement.shadowRootSerializable", "shadowRootSerializable")}}
  - : یک بولی که مقدار ویژگی [`shadowrootserializable`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootserializable) در عنصر `<template>` مرتبط را بازتاب می‌دهد.
- {{domxref("HTMLTemplateElement.shadowRootSlotAssignment", "shadowRootSlotAssignment")}}
  - : رشته‌ای که مقدار ویژگی [`shadowrootslotassignment`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootslotassignment) در عنصر `<template>` مرتبط را بازتاب می‌دهد.

## متدهای نمونه

_این رابط، متدهای {{domxref("HTMLElement")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}