---
title: CSS Typed Object Model API
slug: Web/API/CSS_Typed_OM_API
page-type: web-api-overview
browser-compat:
  - api.CSSStyleValue
  - api.StylePropertyMap
  - api.CSSUnparsedValue
  - api.CSSKeywordValue
---

{{DefaultAPISidebar("CSS Typed Object Model API")}}

API مدل شیء تایپ‌شدهٔ CSS (CSS Typed Object Model) دستکاری ویژگی‌های CSS را با در معرض قرار دادن مقادیر CSS به‌عنوان اشیاء جاوااسکریپت تایپ‌شده به‌جای رشته‌ها ساده‌تر می‌کند. این کار نه‌تنها دستکاری CSS را ساده‌تر می‌کند، بلکه تأثیر منفی بر عملکرد را نسبت به {{domxref('HTMLElement.style')}} کاهش می‌دهد.

به‌طور کلی، مقادیر CSS را می‌توان در جاوااسکریپت به‌صورت رشته خواند و نوشت، که می‌تواند کند و دست‌وپاگیر باشد. API مدل شیء تایپ‌شدهٔ CSS رابط‌هایی برای تعامل با مقادیر زیربنایی فراهم می‌کند و آن‌ها را با اشیاء جاوااسکریپت تخصصی نمایش می‌دهد که نسبت به تجزیه و الحاق رشته‌ها آسان‌تر و قابل‌اعتمادتر قابل دستکاری و درک هستند. این کار برای توسعه‌دهندگان ساده‌تر است (مثلاً مقادیر عددی با اعداد واقعی جاوااسکریپت بازتاب می‌شوند و عملیات ریاضی آگاه به واحد برای آن‌ها تعریف شده است). همچنین معمولاً سریع‌تر است، زیرا مقادیر را می‌توان مستقیماً دستکاری کرد و سپس بدون نیاز به ساخت و تجزیه رشته‌های CSS، با هزینه کم به مقادیر زیربنایی بازگرداند.

CSS Typed OM هم امکان دستکاری کارآمد مقادیر اختصاص‌یافته به ویژگی‌های CSS را فراهم می‌کند و هم کدی قابل نگهداری ایجاد می‌کند که هم قابل‌فهم‌تر و هم نوشتن آن آسان‌تر است.

## رابط‌ها

### `CSSStyleValue`

رابط {{domxref('CSSStyleValue')}} در API مدل شیء تایپ‌شدهٔ CSS، کلاس پایه برای همهٔ مقادیر CSS قابل دسترسی از طریق API Typed OM است. نمونه‌ای از این کلاس را می‌توان در هر جایی که انتظار یک رشته می‌رود استفاده کرد.

- {{domxref('CSSStyleValue/parse_static', 'CSSStyleValue.parse()')}}
  - : روشی که امکان ساخت `CSSNumericValue` از یک رشته CSS را فراهم می‌کند. این روش یک ویژگی خاص CSS را به مقادیر مشخص‌شده تنظیم می‌کند و اولین مقدار را به‌عنوان یک شیء `CSSStyleValue` برمی‌گرداند.
- {{domxref('CSSStyleValue.parseAll_static', 'CSSStyleValue.parseAll()')}}
  - : روشی که همهٔ رخدادهای یک ویژگی خاص CSS را به مقدار مشخص‌شده تنظیم می‌کند و آرایه‌ای از اشیاء `CSSStyleValue` برمی‌گرداند که هر کدام یکی از مقادیر ارائه‌شده را شامل می‌شود.

### `StylePropertyMap`

رابط {{domxref('StylePropertyMap')}} در API مدل شیء تایپ‌شدهٔ CSS، نمایشی از یک بلوک اعلان CSS ارائه می‌دهد که جایگزینی برای `CSSStyleDeclaration` است.

- {{domxref('StylePropertyMap.set()')}}
  - : روشی که اعلان CSS مربوط به ویژگی داده‌شده را به مقدار داده‌شده تغییر می‌دهد.
- {{domxref('StylePropertyMap.append()')}}
  - : روشی که یک اعلان CSS جدید با ویژگی و مقدار داده‌شده به `StylePropertyMap` اضافه می‌کند.
- {{domxref('StylePropertyMap.delete()')}}
  - : روشی که اعلان CSS مربوط به ویژگی داده‌شده را از `StylePropertyMap` حذف می‌کند.
- {{domxref('StylePropertyMap.clear()')}}
  - : روشی که همهٔ اعلان‌ها را در `StylePropertyMap` حذف می‌کند.

### `CSSUnparsedValue`

رابط {{domxref('CSSUnparsedValue')}} در API مدل شیء تایپ‌شدهٔ CSS، مقادیر ویژگی‌ای را نشان می‌دهد که به ویژگی‌های سفارشی ارجاع می‌دهند. این رابط شامل فهرستی از تکه‌های رشته و ارجاع به متغیرها است.

- {{domxref("CSSUnparsedValue.CSSUnparsedValue", "CSSUnparsedValue()")}} سازنده
  - : یک شیء `CSSUnparsedValue` جدید می‌سازد که مقادیر ویژگی‌های ارجاع‌دهنده به ویژگی‌های سفارشی را نشان می‌دهد.
- {{domxref('CSSUnparsedValue.entries()')}}
  - : روشی که آرایه‌ای از جفت‌های `[key, value]` ویژگی‌های قابل شمارش خود شیء را به همان ترتیبی که توسط حلقه `for...in` ارائه می‌شود برمی‌گرداند (تفاوت این است که حلقه for-in ویژگی‌های زنجیره پروتوتایپ را نیز شمارش می‌کند).
- {{domxref('CSSUnparsedValue.forEach()')}}
  - : روشی که یک تابع ارائه‌شده را یک بار برای هر عنصر از `CSSUnparsedValue` اجرا می‌کند.
- {{domxref('CSSUnparsedValue.keys()')}}
  - : روشی که یک شیء _تکرارگر آرایه_ جدید برمی‌گرداند که کلیدهای هر اندیس در آرایه را شامل می‌شود.

### سریال‌سازی `CSSKeywordValue`

رابط {{domxref('CSSKeywordValue')}} در API مدل شیء تایپ‌شدهٔ CSS، یک شیء برای نمایش کلیدواژه‌های CSS و دیگر شناسه‌ها ایجاد می‌کند.

- {{domxref("CSSKeywordValue.CSSKeywordValue", "CSSKeywordValue()")}} سازنده
  - : سازنده، یک شیء {{domxref("CSSKeywordValue.CSSKeywordValue", "CSSKeywordValue()")}} جدید ایجاد می‌کند که کلیدواژه‌های CSS و دیگر شناسه‌ها را نشان می‌دهد.
- {{domxref('CSSKeywordValue.value()')}}
  - : ویژگی از رابط `CSSKeywordValue` که مقدار `CSSKeywordValue` را برمی‌گرداند یا تنظیم می‌کند.

## رابط‌های CSSStyleValue

{{domxref('CSSStyleValue')}} کلاس پایه‌ای است که همهٔ مقادیر CSS از طریق آن بیان می‌شوند. زیرکلاس‌ها عبارت‌اند از:

- {{domxref('CSSImageValue')}}
  - : رابطی که مقادیر ویژگی‌های تصویرپذیر مانند {{cssxref("background-image")}}، {{cssxref("list-style-image")}} یا {{cssxref("border-image-source")}} را نشان می‌دهد.
- {{domxref('CSSKeywordValue')}}
  - : رابطی که یک شیء برای نمایش کلیدواژه‌های CSS و دیگر شناسه‌ها ایجاد می‌کند. وقتی در جایی که انتظار یک رشته می‌رود استفاده شود، مقدار `CSSKeyword.value` را برمی‌گرداند.
- {{domxref('CSSMathValue')}}
  - : درختی از زیرکلاس‌ها که مقادیر عددی پیچیده‌تر از یک مقدار و واحد را نشان می‌دهند، از جمله:
    - {{domxref('CSSMathMax')}} - تابع {{cssxref("max","max()")}} را نشان می‌دهد.
    - {{domxref('CSSMathMin')}} - تابع {{cssxref("min","min()")}} را نشان می‌دهد.
    - {{domxref('CSSMathClamp')}} - تابع {{cssxref("clamp","clamp()")}} را نشان می‌دهد.
    - {{domxref('CSSMathNegate')}} - مقدار ورودی را منفی می‌کند.
    - {{domxref('CSSMathInvert')}} - مقدار {{cssxref("calc","calc()")}} را که به‌صورت `calc(1 / <value>)` استفاده می‌شود نشان می‌دهد. این نوع به‌صورت داخلی توسط {{domxref('CSSNumericValue.div','div()')}} برای ایجاد یک {{domxref('CSSMathProduct')}} مناسب استفاده می‌شود.
    - {{domxref('CSSMathProduct')}} - نتیجهٔ حاصل از فراخوانی {{domxref('CSSNumericValue.mul','mul()')}} یا {{domxref('CSSNumericValue.div','div()')}} روی {{domxref('CSSNumericValue')}} را نشان می‌دهد.
    - {{domxref('CSSMathSum')}} - نتیجهٔ حاصل از فراخوانی {{domxref('CSSNumericValue.add','add()')}}، {{domxref('CSSNumericValue.sub','sub()')}} یا {{domxref('CSSNumericValue.toSum','toSum()')}} روی {{domxref('CSSNumericValue')}} را نشان می‌دهد.

- {{domxref('CSSNumericValue')}}
  - : رابطی که عملیات قابل انجام توسط همهٔ مقادیر عددی را نشان می‌دهد، از جمله:
    - {{domxref('CSSNumericValue.add')}} - اعداد داده‌شده را به `CSSNumericValue` اضافه می‌کند.
    - {{domxref('CSSNumericValue.sub')}} - اعداد داده‌شده را از `CSSNumericValue` کم می‌کند.
    - {{domxref('CSSNumericValue.mul')}} - اعداد داده‌شده را در `CSSNumericValue` ضرب می‌کند.
    - {{domxref('CSSNumericValue.div')}} - `CSSNumericValue` را بر مقدار داده‌شده تقسیم می‌کند و اگر `0` باشد خطا می‌دهد.
    - {{domxref('CSSNumericValue.min')}} - کمترین مقدار داده‌شده را برمی‌گرداند
    - {{domxref('CSSNumericValue.max')}} - بیشترین مقدار داده‌شده را برمی‌گرداند
    - {{domxref('CSSNumericValue.equals')}} - اگر همهٔ مقادیر دقیقاً از نوع و مقدار یکسان و به همان ترتیب باشند `true` و در غیر این صورت `false` برمی‌گرداند
    - {{domxref('CSSNumericValue.to')}} - `value` را به مقدار دیگری با _واحد_ مشخص‌شده تبدیل می‌کند.
    - {{domxref('CSSNumericValue.toSum')}}
    - {{domxref('CSSNumericValue.type')}}
    - {{domxref('CSSNumericValue/parse_static', 'CSSNumericValue.parse')}} - عددی را که از یک رشته CSS تجزیه شده برمی‌گرداند

- {{domxref('CSSPositionValue')}}
  - : مقادیر ویژگی‌هایی را نشان می‌دهد که یک موقعیت می‌گیرند، مانند object-position.
- {{domxref('CSSTransformValue')}}
  - : رابطی که فهرستی از مقادیر {{cssxref("transform")}} را نشان می‌دهد. آن‌ها یک یا چند {{domxref('CSSTransformComponent')}} را «شامل» می‌شوند که مقادیر تابع `transform` جداگانه را نشان می‌دهند.
- {{domxref('CSSUnitValue')}}
  - : رابطی که مقادیر عددی قابل نمایش به‌صورت یک واحد، یا یک عدد نام‌گذاری‌شده و درصد را نشان می‌دهد.
- {{domxref('CSSUnparsedValue')}}
  - : مقادیر ویژگی‌هایی را نشان می‌دهد که به [ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) ارجاع می‌دهند. این مقادیر شامل فهرستی از تکه‌های رشته و ارجاع به متغیرها هستند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API)
- [Using the CSS Typed Object Model](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Houdini](/en-US/docs/Web/API/Houdini_APIs)