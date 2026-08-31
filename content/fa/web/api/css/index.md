---
title: CSS
slug: Web/API/CSS
page-type: web-api-interface
browser-compat: api.CSS
---

{{APIRef("CSSOM")}}

اینترفیس **`CSS`** شامل متدهای کاربردی مرتبط با CSS است. هیچ شیئی با این اینترفیس پیاده‌سازی نمی‌شود؛ این اینترفیس فقط متدهای استاتیک دارد و بنابراین یک اینترفیس کاربردی (Utility) محسوب می‌شود.

## ویژگی‌های استاتیک

- {{DOMxRef("CSS/highlights_static", "CSS.highlights")}}
  - : دسترسی به `HighlightRegistry` را فراهم می‌کند که برای استایل‌دهی به محدوده‌های متنی دلخواه با استفاده از {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}} به کار می‌رود.
- {{DOMxRef("CSS/paintWorklet_static", "CSS.paintWorklet")}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : دسترسی به Worklet مسئول تمام کلاس‌های مرتبط با نقاشی (Painting) را فراهم می‌کند.

## ویژگی‌های نمونه

_اینترفیس CSS یک اینترفیس کاربردی است و هیچ شیئی از این نوع نمی‌تواند ساخته شود؛ فقط ویژگی‌های استاتیک روی آن تعریف شده‌اند._

## متدهای استاتیک

_هیچ متد استاتیک به ارث‌رسیده‌ای وجود ندارد._

- {{DOMxRef("CSS/registerProperty_static", "CSS.registerProperty()")}}
  - : [ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) را ثبت می‌کند و امکان بررسی نوع ویژگی، مقادیر پیش‌فرض، و ویژگی‌هایی که مقدار خود را به ارث می‌برند یا نمی‌برند، فراهم می‌سازد.
- {{DOMxRef("CSS/supports_static", "CSS.supports()")}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد جفت _ویژگی-مقدار_ یا شرط داده‌شده در پارامتر پشتیبانی می‌شود یا خیر.
- {{DOMxRef("CSS/escape_static", "CSS.escape()")}}
  - : برای فرار (escape) دادن یک رشته استفاده می‌شود، عمدتاً برای استفاده به عنوان بخشی از یک انتخابگر CSS.
- [توابع کارخانه‌ای CSS](/en-US/docs/Web/API/CSS/factory_functions_static)
  - : برای بازگرداندن یک [`CSSUnitValue`](/en-US/docs/Web/API/CSSUnitValue) جدید با مقدار عددی برابر با پارامتر داده‌شده برحسب واحد نام متد تابع کارخانه‌ای استفاده می‌شوند.

    ```js
    CSS.em(3); // CSSUnitValue {value: 3, unit: "em"}
    ```

## متدهای نمونه

_اینترفیس CSS یک اینترفیس کاربردی است و هیچ شیئی از این نوع نمی‌تواند ساخته شود؛ فقط متدهای استاتیک روی آن تعریف شده‌اند._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}