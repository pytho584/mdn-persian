---
title: "CSSStyleValue"
slug: Web/API/CSSStyleValue
page-type: web-api-interface
browser-compat: api.CSSStyleValue

---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

اینترفیس **`CSSStyleValue`** در [مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Typed_OM_API)، کلاس پایهٔ تمام مقادیر CSS است که از طریق API مدل شیء تایپ‌شده در دسترس هستند. یک نمونه از این کلاس را می‌توان هر جا که یک رشته (string) انتظار می‌رود استفاده کرد.

## روش‌های ایستا

- [`CSSStyleValue.parse()`](/en-US/docs/Web/API/CSSStyleValue/parse_static)
  - : یک ویژگی CSS مشخص را با مقادیر داده‌شده تنظیم می‌کند و اولین مقدار را به‌عنوان یک شیء `CSSStyleValue` برمی‌گرداند.
- [`CSSStyleValue.parseAll()`](/en-US/docs/Web/API/CSSStyleValue/parseAll_static)
  - : همهٔ رخدادهای یک ویژگی CSS مشخص را با مقدار داده‌شده تنظیم می‌کند و آرایه‌ای از اشیاء `CSSStyleValue` برمی‌گرداند که هر کدام یکی از مقادیر ارائه‌شده را شامل می‌شود.

## روش‌های نمونه

- {{domxref("CSSStyleValue.toString()")}}
  - : یک {{Glossary("stringifier")}} که مقدار را به‌صورت رشته‌ای از متن استاندارد CSS برمی‌گرداند.

## اینترفیس‌های مبتنی بر CSSStyleValue

- {{domxref('CSSImageValue')}}
- {{domxref('CSSKeywordValue')}}
- {{domxref('CSSNumericValue')}}
- {{domxref('CSSPositionValue')}}
- {{domxref('CSSTransformValue')}}
- {{domxref('CSSUnparsedValue')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}