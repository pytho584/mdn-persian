---
title: "CSS Object Model (CSSOM)"
slug: Web/API/CSS_Object_Model
page-type: web-api-overview
spec-urls:
  - https://drafts.csswg.org/cssom/
  - https://drafts.csswg.org/cssom-view/
  - https://drafts.css-houdini.org/css-typed-om/
---

{{DefaultAPISidebar("CSSOM")}}

**CSS Object Model** (مدل شیءِ CSS) مجموعه‌ای از APIها است که دستکاری CSS را از طریق جاوااسکریپت ممکن می‌سازد. این مدل شباهت زیادی به DOM دارد، با این تفاوت که به‌جای HTML، به CSS مربوط می‌شود. کاربران می‌توانند به‌کمک آن، استایل‌های CSS را به‌صورت پویا بخوانند و اصلاح کنند.

مقادیر CSS بدون نوع (untyped) نمایش داده می‌شوند؛ به این معنی که با استفاده از اشیاء {{JSxRef("String")}} نشان داده می‌شوند.

## مرجع

- {{DOMxRef("AnimationEvent")}}
- {{DOMxRef("CaretPosition")}}
- {{DOMxRef("CSS")}}
- {{DOMxRef("CSSConditionRule")}}
- {{DOMxRef("CSSCounterStyleRule")}}
- {{DOMxRef("CSSFontFaceDescriptors")}}
- {{DOMxRef("CSSFontFaceRule")}}
- {{DOMxRef("CSSFontFeatureValuesMap")}}
- {{DOMxRef("CSSFontFeatureValuesRule")}}
- {{DOMxRef("CSSFunctionDeclarations")}}
- {{DOMxRef("CSSFunctionDescriptors")}}
- {{DOMxRef("CSSFunctionRule")}}
- {{DOMxRef("CSSGroupingRule")}}
- {{DOMxRef("CSSImportRule")}}
- {{DOMxRef("CSSKeyframeRule")}}
- {{DOMxRef("CSSKeyframesRule")}}
- {{DOMxRef("CSSMarginRule")}}
- {{DOMxRef("CSSMediaRule")}}
- {{DOMxRef("CSSNamespaceRule")}}
- {{DOMxRef("CSSPageRule")}}
- {{DOMxRef("CSSPositionTryRule")}}
- {{DOMxRef("CSSPositionTryDescriptors")}}
- {{DOMxRef("CSSRule")}}
- {{DOMxRef("CSSRuleList")}}
- {{DOMxRef("CSSStartingStyleRule")}}
- {{DOMxRef("CSSStyleDeclaration")}}
- {{DOMxRef("CSSStyleSheet")}}
- {{DOMxRef("CSSStyleRule")}}
- {{DOMxRef("CSSSupportsRule")}}
- {{DOMXRef("CSSNestedDeclarations")}}
- {{DOMxRef("FontFace")}}
- {{DOMxRef("FontFaceSet")}}
- {{DOMxRef("FontFaceSetLoadEvent")}}
- {{DOMxRef("MediaList")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}
- {{DOMxRef("Screen")}}
- {{DOMxRef("StyleSheet")}}
- {{DOMxRef("StyleSheetList")}}
- {{DOMxRef("TransitionEvent")}}
- {{DOMxRef("VisualViewport")}}

چندین رابط دیگر نیز به‌وسیلهٔ مشخصات مرتبط با CSSOM گسترش یافته‌اند: {{DOMxRef("Document")}}، {{DOMxRef("Window")}}، {{DOMxRef("Element")}}، {{DOMxRef("HTMLElement")}}، {{DOMxRef("HTMLImageElement")}}، {{DOMxRef("Range")}}، {{DOMxRef("MouseEvent")}} و {{DOMxRef("SVGElement")}}.

### CSS Typed Object Model

- {{DOMxRef("CSSImageValue")}}
- {{DOMxRef("CSSKeywordValue")}}
- {{DOMxRef("CSSMathClamp")}}
- {{DOMxRef("CSSMathInvert")}}
- {{DOMxRef("CSSMathMax")}}
- {{DOMxRef("CSSMathMin")}}
- {{DOMxRef("CSSMathNegate")}}
- {{DOMxRef("CSSMathProduct")}}
- {{DOMxRef("CSSMathSum")}}
- {{DOMxRef("CSSMathValue")}}
- {{DOMxRef("CSSMatrixComponent")}}
- {{DOMxRef("CSSNumericArray")}}
- {{DOMxRef("CSSNumericValue")}}
- {{DOMxRef("CSSPerspective")}}
- {{DOMxRef("CSSPositionValue")}}
- {{DOMxRef("CSSRotate")}}
- {{DOMxRef("CSSScale")}}
- {{DOMxRef("CSSSkew")}}
- {{DOMxRef("CSSSkewX")}}
- {{DOMxRef("CSSSkewY")}}
- {{DOMxRef("CSSStyleValue")}}
- {{DOMxRef("CSSTransformComponent")}}
- {{DOMxRef("CSSTransformValue")}}
- {{DOMxRef("CSSTranslate")}}
- {{DOMxRef("CSSUnitValue")}}
- {{DOMxRef("CSSUnparsedValue")}}
- {{DOMxRef("CSSVariableReferenceValue")}}
- {{DOMxRef("StylePropertyMap")}}
- {{DOMxRef("StylePropertyMapReadOnly")}}

### رابط‌های منسوخ CSSOM {{deprecated_inline}}

{{deprecated_header}}

- {{DOMxRef("CSSPrimitiveValue")}} {{deprecated_inline}}
- {{DOMxRef("CSSValue")}} {{deprecated_inline}}
- {{DOMxRef("CSSValueList")}} {{deprecated_inline}}

## آموزش‌ها

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- [مدیریت جهت‌گیری صفحه‌نمایش](/en-US/docs/Web/API/CSS_Object_Model/Managing_screen_orientation)

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

تمامی این ویژگی‌ها در طول سال‌ها و به‌تدریج به مرورگرهای مختلف اضافه شده‌اند؛ این فرایند نسبتاً پیچیده‌ای است که نمی‌توان آن را در یک جدول ساده خلاصه کرد. لطفاً برای اطلاع از میزان در دسترس بودن هر یک، به صفحهٔ همان رابط مراجعه کنید.

## همچنین ببینید

- [Document Object Model (DOM)](/en-US/docs/Web/API/Document_Object_Model)
- [Houdini APIs](/en-US/docs/Web/API/Houdini_APIs)