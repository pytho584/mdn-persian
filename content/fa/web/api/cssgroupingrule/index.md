---
title: CSSGroupingRule
slug: Web/API/CSSGroupingRule
page-type: web-api-interface
browser-compat: api.CSSGroupingRule
---

{{ APIRef("CSSOM") }}

رابط **`CSSGroupingRule`** در [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) نشان‌دهنده‌ی هر [قاعده‌ی at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) در CSS است که شامل قواعد دیگری درون خود باشد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های {{domxref("CSSRule")}} را به ارث می‌برد._

- {{domxref("CSSGroupingRule.cssRules")}} {{ReadOnlyInline}}
  - : یک {{domxref("CSSRuleList")}} از قواعد CSS موجود در قاعده‌ی رسانه (media rule) را برمی‌گرداند.

## روش‌های نمونه

_این رابط همچنین روش‌های {{domxref("CSSRule")}} را به ارث می‌برد._

- {{domxref("CSSGroupingRule.deleteRule")}}
  - : یک قاعده را از شیوه‌نامه حذف می‌کند.
- {{domxref("CSSGroupingRule.insertRule")}}
  - : یک قاعده‌ی سبک جدید را به شیوه‌نامه‌ی جاری اضافه می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از اطلاعات سبک‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)