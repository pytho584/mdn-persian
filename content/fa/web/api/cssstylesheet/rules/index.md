---
title: "CSSStyleSheet: rules property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleSheet/rules"
---

---
title: "CSSStyleSheet: rules property"
short-title: rules
slug: Web/API/CSSStyleSheet/rules
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.CSSStyleSheet.rules
---

{{APIRef("CSSOM")}}{{deprecated_header}}

**`rules`** یک _ویژگی قدیمی_ و _منسوخشده_ در رابط {{domxref("CSSStyleSheet")}} است. این ویژگی از نظر عملکردی با ویژگی ترجیحی {{domxref("CSSStyleSheet.cssRules", "cssRules")}} یکسان است و دسترسی به فهرستی را فراهم میکند که بهصورت زنده بهروزرسانی میشود و شامل قوانین CSS تشکیلدهندهٔ شیوهنامه (stylesheet) است.

> [!NOTE]
> بهعنوان یک ویژگی قدیمی، نباید از `rules` استفاده کنید و بهجای آن باید از ویژگی ترجیحی {{domxref("CSSStyleSheet.cssRules", "cssRules")}} بهره ببرید. اگرچه بعید است که `rules` بهزودی حذف شود، اما پشتیبانی از آن بهاندازهٔ کافی گسترده نیست و استفاده از آن میتواند مشکلات سازگاری برای سایت یا برنامهٔ شما ایجاد کند.

## مقدار

یک {{domxref("CSSRuleList")}} با بهروزرسانی زنده که شامل هر یک از قوانین CSS تشکیلدهندهٔ شیوهنامه است. هر ورودی در این فهرست قوانین، یک شیء {{domxref("CSSRule")}} است که یک قانون از قوانین سازندهٔ شیوهنامه را توصیف میکند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model)
- [استفاده از اطلاعات استایلدهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)
