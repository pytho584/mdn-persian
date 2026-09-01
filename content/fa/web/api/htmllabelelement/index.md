---
title: HTMLLabelElement
slug: Web/API/HTMLLabelElement
page-type: web-api-interface
browser-compat: api.HTMLLabelElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLLabelElement`** به ویژگی‌های خاص عناصر {{HTMLElement("label")}} دسترسی می‌دهد. این رابط متدها و ویژگی‌های خود را از رابط پایه {{domxref("HTMLElement")}} به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌هایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLLabelElement.control")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLElement")}} که نشان‌دهنده کنترلی است که برچسب با آن مرتبط است.
- {{domxref("HTMLLabelElement.form")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("HTMLFormElement")}} که فرم مرتبط با کنترل برچسب‌گذاری شده را نشان می‌دهد، یا `null` اگر هیچ کنترلی مرتبط نباشد، یا اگر آن کنترل با فرمی مرتبط نباشد. به عبارت دیگر، این یک میان‌بر برای `HTMLLabelElement.control.form` است.
- {{domxref("HTMLLabelElement.htmlFor")}}
  - : یک رشته شامل شناسه (ID) کنترل برچسب‌گذاری شده. این ویژگی منعکس‌کننده ویژگی [`for`](/en-US/docs/Web/HTML/Reference/Elements/label#for) است.

> [!NOTE]
> برای تنظیم برنامه‌نویسی ویژگی `for`، از [`htmlFor`](/en-US/docs/Web/API/HTMLLabelElement/htmlFor) استفاده کنید.

## روش‌های نمونه

_متد خاصی ندارد؛ متدها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("label")}}
- {{HTMLElement("form")}}
- {{domxref("HTMLFormElement")}}