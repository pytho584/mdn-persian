---
title: CSSCounterStyleRule
slug: Web/API/CSSCounterStyleRule
page-type: web-api-interface
browser-compat: api.CSSCounterStyleRule
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSCounterStyleRule`** نمایانگر یک [قانون at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{CSSxRef("@counter-style")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های والد خود، {{DOMxRef("CSSRule")}} را به ارث می‌برد._

- {{DOMxRef("CSSCounterStyleRule.name")}}
  - : رشته‌ای که شامل سریال‌سازی {{CSSxRef("&lt;custom-ident&gt;")}} تعریف‌شده به‌عنوان `name` برای قانون مرتبط است.
- {{DOMxRef("CSSCounterStyleRule.system")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/system", "system")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.symbols")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/symbols", "symbols")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.additiveSymbols")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/additive-symbols", "additive-symbols")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.negative")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/negative", "negative")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.prefix")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/prefix", "prefix")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.suffix")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/suffix", "suffix")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.range")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/range", "range")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.pad")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/pad", "pad")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.speakAs")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/speak-as", "speak-as")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.
- {{DOMxRef("CSSCounterStyleRule.fallback")}}
  - : رشته‌ای که شامل سریال‌سازی توصیفگر {{CSSxRef("@counter-style/fallback", "fallback")}} تعریف‌شده برای قانون مرتبط است. اگر این توصیفگر در قانون مرتبط مشخص نشده باشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.

## روش‌های نمونه

_این رابط هیچ روش خاصی را پیاده‌سازی نمی‌کند، اما روش‌های والد خود، {{DOMxRef("CSSRule")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{CSSxRef("@counter-style")}}
- ماژول [سبک‌های شمارندهٔ CSS](/en-US/docs/Web/CSS/Guides/Counter_styles)
- راهنمای [استفاده از شمارنده‌های CSS](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters)