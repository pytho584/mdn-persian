---
title: CSSPrimitiveValue
slug: Web/API/CSSPrimitiveValue
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

رابط **`CSSPrimitiveValue`** از رابط {{DOMxRef("CSSValue")}} مشتق شده است و مقدار محاسبه‌شدهٔ فعلی یک ویژگی CSS را نشان می‌دهد.

> [!NOTE]
> این اینترفیس بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش رها شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود، می‌توانید از موارد زیر استفاده کنید:
>
> - [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیء CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) جدید که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

این اینترفیس یک مقدار CSS تکی را نمایش می‌دهد. می‌توان از آن برای تعیین مقدار یک ویژگی استایل خاص که در حال حاضر در یک بلاک تنظیم شده است استفاده کرد، یا می‌توان یک ویژگی استایل خاص را به‌طور صریح درون بلاک تنظیم کرد. یک نمونه از این اینترفیس را می‌توان از روش {{DOMxRef("CSSStyleDeclaration.getPropertyCSSValue()", "getPropertyCSSValue()")}} در اینترفیس {{DOMxRef("CSSStyleDeclaration")}} به‌دست آورد. یک شیء `CSSPrimitiveValue` فقط در زمینهٔ یک ویژگی CSS ظاهر می‌شود.

تبدیل بین مقادیر مطلق مجاز است (از میلی‌متر به سانتی‌متر، از درجه به رادیان، و غیره) اما بین مقادیر نسبی مجاز نیست. (به عنوان مثال، یک مقدار پیکسل نمی‌تواند به مقدار سانتی‌متر تبدیل شود.) مقادیر درصدی قابل تبدیل نیستند زیرا نسبت به مقدار والد (یا مقدار ویژگی دیگر) تعریف می‌شوند. یک استثنا برای مقادیر درصدی رنگ وجود دارد: از آنجا که مقدار درصدی رنگ نسبت به محدوده ۰ تا ۲۵۵ است، یک مقدار درصدی رنگ می‌تواند به عدد تبدیل شود (همچنین به اینترفیس {{DOMxRef("RGBColor")}} مراجعه کنید).

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{DOMxRef("CSSValue")}}، به ارث می‌برد._

- {{DOMxRef("CSSPrimitiveValue.primitiveType")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک `unsigned short` که نوع مقدار را نشان می‌دهد. مقادیر ممکن عبارتند از:

    | Constant         | توصیف                                                                                                                                                                       |
    | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `CSS_ATTR`       | مقدار یک تابع {{CSSxRef("attr", "attr()")}} است. مقدار را می‌توان با استفاده از روش `getStringValue()` به‌دست آورد.                                                   |
    | `CSS_CM`         | مقدار یک {{CSSxRef("&lt;length&gt;")}} در سانتی‌متر است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                               |
    | `CSS_COUNTER`    | مقدار یک تابع [counter یا counters](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters) است. مقدار را می‌توان با استفاده از روش `getCounterValue()` به‌دست آورد. |
    | `CSS_DEG`        | مقدار یک {{CSSxRef("&lt;angle&gt;")}} در درجه است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                   |
    | `CSS_DIMENSION`  | مقدار یک {{CSSxRef("&lt;number&gt;")}} با بُعد ناشناخته است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                    |
    | `CSS_EMS`        | مقدار یک {{CSSxRef("&lt;length&gt;")}} در واحد em است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                  |
    | `CSS_EXS`        | مقدار یک {{CSSxRef("&lt;length&gt;")}} در واحد ex است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                  |
    | `CSS_GRAD`       | مقدار یک {{CSSxRef("&lt;angle&gt;")}} در گراد است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                     |
    | `CSS_HZ`         | مقدار یک {{CSSxRef("&lt;frequency&gt;")}} در هرتز است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                      |
    | `CSS_IDENT`      | مقدار یک شناسه است. مقدار را می‌توان با استفاده از روش `getStringValue()` به‌دست آورد.                                                                               |
    | `CSS_IN`         | مقدار یک {{CSSxRef("&lt;length&gt;")}} در اینچ است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                    |
    | `CSS_KHZ`        | مقدار یک {{CSSxRef("&lt;frequency&gt;")}} در کیلوهرتز است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                              |
    | `CSS_MM`         | مقدار یک {{CSSxRef("&lt;length&gt;")}} در میلی‌متر است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                               |
    | `CSS_MS`         | مقدار یک {{CSSxRef("&lt;time&gt;")}} در میلی‌ثانیه است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                |
    | `CSS_NUMBER`     | مقدار یک {{CSSxRef("&lt;number&gt;")}} ساده است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                       |
    | `CSS_PC`         | مقدار یک {{CSSxRef("&lt;length&gt;")}} در پیکا است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                     |
    | `CSS_PERCENTAGE` | مقدار یک {{CSSxRef("&lt;percentage&gt;")}} است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                          |
    | `CSS_PT`         | مقدار یک {{CSSxRef("&lt;length&gt;")}} در پوینت است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                    |
    | `CSS_PX`         | مقدار یک {{CSSxRef("&lt;length&gt;")}} در پیکسل است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                    |
    | `CSS_RAD`        | مقدار یک {{CSSxRef("&lt;angle&gt;")}} در رادیان است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                   |
    | `CSS_RECT`       | مقدار یک تابع {{CSSxRef("shape", "rect()", "#Syntax")}} است. مقدار را می‌توان با استفاده از روش `getRectValue()` به‌دست آورد.                                          |
    | `CSS_RGBCOLOR`   | مقدار یک {{CSSxRef("&lt;color&gt;")}} است. مقدار را می‌توان با استفاده از روش `getRGBColorValue()` به‌دست آورد.                                                           |
    | `CSS_S`          | مقدار یک {{CSSxRef("&lt;time&gt;")}} در ثانیه است. مقدار را می‌توان با استفاده از روش `getFloatValue()` به‌دست آورد.                                                     |
    | `CSS_STRING`     | مقدار یک {{CSSxRef("&lt;string&gt;")}} است. مقدار را می‌توان با استفاده از روش `getStringValue()` به‌دست آورد.                                                             |
    | `CSS_UNKNOWN`    | مقدار یک مقدار CSS2 شناخته‌شده نیست. مقدار فقط با استفاده از ویژگی {{DOMxRef("CSSValue.cssText", "cssText")}} قابل دریافت است.                                 |
    | `CSS_URI`        | مقدار یک {{cssxref("url_value", "&lt;url&gt;")}} است. مقدار را می‌توان با استفاده از روش `getStringValue()` به‌دست آورد.                                                   |

## روش‌های نمونه

- {{DOMxRef("CSSPrimitiveValue.getCounterValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : این روش برای دریافت مقدار [counter](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters) استفاده می‌شود. اگر این مقدار CSS حاوی مقدار counter نباشد، یک {{DOMxRef("DOMException")}} پرتاب می‌شود. اصلاح ویژگی استایل متناظر را می‌توان با استفاده از اینترفیس {{DOMxRef("Counter")}} انجام داد.
- {{DOMxRef("CSSPrimitiveValue.getFloatValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : این روش برای دریافت یک مقدار اعشاری در یک واحد مشخص استفاده می‌شود. اگر این مقدار CSS حاوی مقدار اعشاری نباشد یا نتوان آن را به واحد مشخص‌شده تبدیل کرد، یک {{DOMxRef("DOMException")}} پرتاب می‌شود.
- {{DOMxRef("CSSPrimitiveValue.getRGBColorValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : این روش برای دریافت رنگ RGB استفاده می‌شود. اگر این مقدار CSS حاوی مقدار رنگ RGB نباشد، یک {{DOMxRef("DOMException")}} پرتاب می‌شود. اصلاح ویژگی استایل متناظر را می‌توان با استفاده از اینترفیس {{DOMxRef("RGBColor")}} انجام داد.
- {{DOMxRef("CSSPrimitiveValue.getRectValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : این روش برای دریافت مقدار Rect استفاده می‌شود. اگر این مقدار CSS حاوی مقدار rect نباشد، یک {{DOMxRef("DOMException")}} پرتاب می‌شود. اصلاح ویژگی استایل متناظر را می‌توان با استفاده از اینترفیس {{DOMxRef("Rect")}} انجام داد.
- {{DOMxRef("CSSPrimitiveValue.getStringValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : این روش برای دریافت مقدار رشته استفاده می‌شود. اگر مقدار CSS حاوی مقدار رشته نباشد، یک {{DOMxRef("DOMException")}} پرتاب می‌شود.
- {{DOMxRef("CSSPrimitiveValue.setFloatValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : روشی برای تنظیم مقدار اعشاری با یک واحد مشخص. اگر ویژگی متصل به این مقدار نتواند واحد مشخص‌شده یا مقدار اعشاری را بپذیرد، مقدار بدون تغییر می‌ماند و یک {{DOMxRef("DOMException")}} پرتاب می‌شود.
- {{DOMxRef("CSSPrimitiveValue.setStringValue()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : روشی برای تنظیم مقدار رشته با واحد مشخص. اگر ویژگی متصل به این مقدار نتواند واحد مشخص‌شده یا مقدار رشته را بپذیرد، مقدار بدون تغییر می‌ماند و یک {{DOMxRef("DOMException")}} پرتاب می‌شود.

## مشخصات

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش استانداردسازی حذف شده است.

این ویژگی با API [CSS Typed Object Model](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است که اکنون در مسیر استاندارد قرار دارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("CSSValue")}}
- {{DOMxRef("CSSValueList")}}