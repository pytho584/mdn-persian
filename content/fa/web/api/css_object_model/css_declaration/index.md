---
title: "CSS Declaration"
slug: Web/API/CSS_Object_Model/CSS_Declaration
page-type: guide
spec-urls: https://drafts.csswg.org/cssom/#css-declarations
---

{{DefaultAPISidebar("CSSOM")}}

**اعلان CSS** (CSS declaration) یک مفهوم انتزاعی است که به‌عنوان یک شیء در DOM در دسترس نیست. این مفهوم بیانگر جفت‌شدن یک ویژگی و مقدار CSS است.

یک اعلان CSS ویژگی‌های مرتبط زیر را دارد:

- نام ویژگی
  - : نام ویژگیِ اعلان، مانند {{cssxref("background-color")}}.
- مقدار
  - : مقدار اعلان به‌صورت فهرستی از مقادیر مؤلفه‌ای.
- پرچم مهم (important flag)
  - : یا تنظیم شده است یا تنظیم نشده.
- پرچم حساس به بزرگی/کوچکی حروف (case-sensitive flag)
  - : اگر نام ویژگی طبق مشخصات به‌عنوان حساس به بزرگی/کوچکی حروف تعریف شده باشد، تنظیم می‌شود؛ در غیر این صورت تنظیم نمی‌شود.

## مثال پایه

مثال زیر یک قانون CSS را با [بلوک اعلان‌های CSS](/en-US/docs/Web/API/CSS_Object_Model/CSS_Declaration_Block) برای عنصر {{htmlelement("Heading_Elements","&lt;h1&gt;")}} نشان می‌دهد. بلوک اعلان‌های CSS خطوط بین آکولادهاست که شامل دو اعلان CSS است: یکی برای {{cssxref("font-style")}} و دیگری برای {{cssxref("color")}}.

```css
h1 {
  font-style: italic;
  color: rebeccapurple;
}
```

## مشخصات

{{Specifications}}