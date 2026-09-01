---
title: HTMLParamElement
slug: Web/API/HTMLParamElement
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.HTMLParamElement
---

{{APIRef("HTML DOM")}}{{Deprecated_Header}}

رابط **`HTMLParamElement`** ویژگی‌های خاصی (فراتر از ویژگی‌های رابط معمول {{domxref("HTMLElement")}} که از آن به ارث می‌برد) برای دستکاری عناصر {{HTMLElement("param")}} فراهم می‌کند. این عناصر یک جفت کلید و مقدار را نشان می‌دهند که به عنوان پارامتری برای یک عنصر {{HTMLElement("object")}} عمل می‌کنند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLParamElement.name")}} {{Deprecated_Inline}}
  - : یک رشته که نام پارامتر را نشان می‌دهد. این ویژگی منعکس‌کنندهٔ ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/param#name) است.
- {{domxref("HTMLParamElement.value")}} {{Deprecated_Inline}}
  - : یک رشته که مقدار مرتبط با پارامتر را نشان می‌دهد. این ویژگی منعکس‌کنندهٔ ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/param#value) است.
- {{domxref("HTMLParamElement.type")}} {{Deprecated_Inline}}
  - : یک رشته شامل نوع پارامتر زمانی که `valueType` مقدار `"ref"` را داشته باشد. این ویژگی منعکس‌کنندهٔ ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/param#type) است.
- {{domxref("HTMLParamElement.valueType")}} {{Deprecated_Inline}}
  - : یک رشته شامل نوع `value`. این ویژگی منعکس‌کنندهٔ ویژگی [`valuetype`](/en-US/docs/Web/HTML/Reference/Elements/param#valuetype) است و یکی از مقادیر `"data"`، `"ref"` یا `"object"` را دارد.

## روش‌های نمونه

_روش خاصی ندارد، روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("param") }}.