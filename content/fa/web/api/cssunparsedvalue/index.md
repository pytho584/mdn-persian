```markdown
---
title: "CSSUnparsedValue"
slug: Web/API/CSSUnparsedValue
page-type: web-api-interface
browser-compat: api.CSSUnparsedValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSUnparsedValue`** از [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) نمایانگر مقادیر ویژگی‌هایی است که به [ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Guides/Cascading_variables) ارجاع می‌دهند. این رابط از فهرستی از قطعات رشته‌ای و ارجاعات متغیر تشکیل شده است.

ویژگی‌های سفارشی توسط `CSSUnparsedValue` و ارجاعات {{cssxref("var", "var()")}} با استفاده از {{domxref('CSSVariableReferenceValue')}} نمایش داده می‌شوند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSUnparsedValue.CSSUnparsedValue", "CSSUnparsedValue()")}}
  - : یک شیء جدید `CSSUnparsedValue` می‌سازد.

## ویژگی‌های نمونه

- {{domxref('CSSUnparsedValue.length')}} {{ReadOnlyInline}}
  - : تعداد آیتم‌های موجود در شیء `CSSUnparsedValue` را بازمی‌گرداند.

## روش‌های نمونه

_همچنین روش‌ها را از رابط والد خود، {{DOMxRef("CSSStyleValue")}} به ارث می‌برد._

- {{domxref('CSSUnparsedValue.entries()')}}
  - : یک آرایه از جفت‌های `[key, value]` ویژگی‌های قابل شمارش خود شیء را به همان ترتیبی که توسط حلقه {{jsxref("Statements/for...in", "for...in")}} ارائه می‌شود، بازمی‌گرداند (تفاوت در این است که حلقه for-in ویژگی‌های موجود در زنجیرهٔ prototype را نیز شمارش می‌کند).
- {{domxref('CSSUnparsedValue.forEach()')}}
  - : یک تابع ارائه‌شده را یک بار برای هر عنصر از شیء `CSSUnparsedValue` اجرا می‌کند.
- {{domxref('CSSUnparsedValue.keys()')}}
  - : یک شیء _تکرارکننده آرایه_ جدید بازمی‌گرداند که شامل کلیدهای هر شاخص در شیء `CSSUnparsedValue` است.
- {{domxref('CSSUnparsedValue.values()')}}
  - : یک شیء _تکرارکننده آرایه_ جدید بازمی‌گرداند که شامل مقادیر هر شاخص در شیء `CSSUnparsedValue` است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CSSImageValue')}}
- {{domxref('CSSKeywordValue')}}
- {{domxref('CSSNumericValue')}}
- {{domxref('CSSPositionValue')}}
- {{domxref('CSSTransformValue')}}
- [Using the CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)
```