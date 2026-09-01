---
title: HTMLStyleElement
slug: Web/API/HTMLStyleElement
page-type: web-api-interface
browser-compat: api.HTMLStyleElement
---

{{APIRef("HTML DOM")}}

رابطهٔ **`HTMLStyleElement`** یک عنصر {{HTMLElement("style")}} را نمایش می‌دهد. این رابط، ویژگی‌ها و روش‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد.

این رابط در بیشتر موارد اجازهٔ دستکاری CSS موجود در عنصر را نمی‌دهد. برای دستکاری CSS، نمای کلی اشیاء مورد استفاده برای دستکاری ویژگی‌های CSS مشخص‌شده با استفاده از DOM را در [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information) ببینید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLStyleElement.blocking")}}
  - : رشته‌ای که نشان می‌دهد برخی عملیات‌ها باید تا زمان دریافت زیرمنابع بحرانی مسدود شوند. این ویژگی، صفت `blocking` عنصر {{HTMLElement("style")}} را منعکس می‌کند.
- {{domxref("HTMLStyleElement.media")}}
  - : رشته‌ای که صفت HTML مربوط به رسانهٔ مقصد مورد نظر برای اطلاعات سبک را منعکس می‌کند.
- {{domxref("HTMLStyleElement.type")}} {{deprecated_inline}}
  - : رشته‌ای که صفت HTML مربوط به نوع سبک اعمال‌شده توسط این دستور را منعکس می‌کند.
- {{domxref("HTMLStyleElement.disabled")}}
  - : یک مقدار بولی که نشان می‌دهد آیا stylesheet مرتبط غیرفعال است یا خیر.
- {{domxref("HTMLStyleElement.sheet")}} {{ReadOnlyInline}}
  - : شیء {{domxref("CSSStyleSheet")}} مرتبط با عنصر داده‌شده را برمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML پیاده‌ساز این رابط: {{HTMLElement("style")}}.
- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information) برای مشاهدهٔ نحوهٔ دستکاری CSS.