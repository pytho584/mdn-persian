---
title: "CSSStyleSheet: addRule() method"
short-title: addRule()
slug: Web/API/CSSStyleSheet/addRule
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.CSSStyleSheet.addRule
---

{{APIRef("CSSOM")}}{{deprecated_header}}

رابط منسوخ‌شدهٔ {{domxref("CSSStyleSheet")}} دارای متد **`addRule()`** (روش قدیمی) است که یک قاعدهٔ جدید به شیوه‌نامه اضافه می‌کند. باید از استفاده از این متد خودداری کنید و به‌جای آن از متد استانداردتر {{domxref("CSSStyleSheet.insertRule", "insertRule()")}} استفاده نمایید.

## نحو (Syntax)

```js-nolint
addRule(selector, styleBlock, index)
```

### پارامترها

- `selector`
  -: یک رشته که بخش انتخاب‌گر (selector) قاعدهٔ CSS را مشخص می‌کند. مقدار پیش‌فرض رشتهٔ `undefined` است.
- `styleBlock`
  -: یک رشته که بلوک سبک (style block) را برای اعمال به عناصر منطبق با `selector` مشخص می‌کند. مقدار پیش‌فرض رشتهٔ `undefined` است.
- `index` {{optional_inline}}
  -: یک شاخص اختیاری در {{domxref("CSSRuleList")}} شیوه‌نامه که قاعدهٔ جدید در آن درج می‌شود. اگر `index` مشخص نشود، از شاخص بعد از آخرین آیتم موجود در فهرست استفاده می‌شود (یعنی مقدار `cssStyleSheet.cssRules.length`).

### مقدار بازگشتی

همیشه ۱- را برمی‌گرداند.

توجه داشته باشید که به دلیل قوانین نسبتاً پیچیده در مورد مکان‌های مجاز برای درج قاعده، ممکن است استثنا (exception) صادر شود. برای اطلاعات بیشتر به {{domxref("CSSStyleSheet.insertRule", "insertRule()")}} مراجعه کنید.

## نکات استفاده

این متد توسط مرورگرها با ساختن یک رشته با استفاده از الگوی literal `` `${selector}{${styleBlock}}` `` و سپس ارسال آن به متد استاندارد {{domxref("CSSStyleSheet.insertRule", "insertRule()")}} پیاده‌سازی می‌شود.

بنابراین، با توجه به کد موجود مانند زیر:

```js
cssStyleSheet.addRule(selector, styles, 0);
```

می‌توانید این را برای استفاده از `insertRule()` استانداردتر به این صورت بازنویسی کنید:

```js
cssStyleSheet.insertRule(`${selector} {${styles}}`, 0);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model)
- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)