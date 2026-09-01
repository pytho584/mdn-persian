---
title: HTMLProgressElement
slug: Web/API/HTMLProgressElement
page-type: web-api-interface
browser-compat: api.HTMLProgressElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLProgressElement`** ویژگی‌ها و متدهای خاصی (فراتر از رابط معمولی {{domxref("HTMLElement")}} که به‌صورت ارث‌بری در اختیار دارد) برای دستکاری چیدمان و نمایش عناصر {{HTMLElement("progress")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLProgressElement.max")}}
  - : یک مقدار `double` که منعکس‌کنندهٔ ویژگی محتوایی همنام است و به اعداد بزرگ‌تر از صفر محدود می‌شود. مقدار پیش‌فرض آن `1.0` است.
- {{domxref("HTMLProgressElement.position")}} {{ReadOnlyInline}}
  - : یک مقدار `double` برمی‌گرداند که حاصل تقسیم مقدار فعلی (`value`) بر حداکثر مقدار (`max`) است؛ اگر نوار پیشرفت نامعین (indeterminate) باشد، `1-` برمی‌گرداند.
- {{domxref("HTMLProgressElement.value")}}
  - : یک مقدار `double` که مقدار فعلی را منعکس می‌کند؛ اگر نوار پیشرفت نامعین باشد، `0` برمی‌گرداند.
- {{domxref("HTMLProgressElement.labels")}} {{ReadOnlyInline}}
  - : یک {{domxref("NodeList")}} حاوی فهرست عناصر {{HTMLElement("label")}} که برچسب‌های این عنصر هستند را برمی‌گرداند.

## روش‌های نمونه

_متد خاصی وجود ندارد؛ متدهای والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("progress")}}