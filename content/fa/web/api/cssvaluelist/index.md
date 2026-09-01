---
title: CSSValueList
slug: Web/API/CSSValueList
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.CSSValueList
---

{{APIRef("CSSOM")}}{{Deprecated_Header}}{{non-standard_header}}

رابطهٔ **`CSSValueList`** از رابط {{DOMxRef("CSSValue")}} مشتق می‌شود و انتزاعی از یک مجموعهٔ مرتب از مقادیر CSS را فراهم می‌کند.

> [!NOTE]
> این رابط بخشی از تلاش برای ایجاد یک مدل شیءِ CSS تایپ‌شده بود. این تلاش کنار گذاشته شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود، می‌توانید از این‌ها استفاده کنید:
>
> - [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ، که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیءِ CSS تایپ‌شدهٔ مدرن](/en-US/docs/Web/API/CSS_Typed_OM_API)، که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

برخی از ویژگی‌ها در نحو (syntax) خود یک لیست خالی را مجاز می‌دانند. در آن صورت، این ویژگی‌ها شناسهٔ `none` را می‌گیرند. بنابراین، یک لیست خالی به این معناست که ویژگی مقدار `none` را دارد.

عناصر موجود در `CSSValueList` از طریق یک شاخص صحیح (integral index) که از ۰ شروع می‌شود، قابل دسترسی هستند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{DOMxRef("CSSValue")}} را به ارث می‌برد._

- {{DOMxRef("CSSValueList.length")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک `unsigned long` که تعداد `CSSValue`های موجود در لیست را نشان می‌دهد.

## روش‌های نمونه

- {{DOMxRef("CSSValueList.item()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : این روش برای بازیابی یک {{DOMxRef("CSSValue")}} با شاخص ترتیبی (ordinal index) استفاده می‌شود. ترتیب در این مجموعه نشان‌دهندهٔ ترتیب مقادیر در ویژگی سبک CSS است. اگر شاخص بزرگ‌تر یا مساوی تعداد مقادیر موجود در لیست باشد، این روش `null` برمی‌گرداند.

## مشخصات

این ویژگی در اصل در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش استانداردسازی حذف شده است.

اکنون با [API مدل شیءِ CSS تایپ‌شدهٔ مدرن](/en-US/docs/Web/API/CSS_Typed_OM_API) که مدرن اما ناسازگار است و در مسیر استاندارد قرار دارد، جایگزین شده است.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMxRef("CSSPrimitiveValue")}}
- {{DOMxRef("CSSValue")}}