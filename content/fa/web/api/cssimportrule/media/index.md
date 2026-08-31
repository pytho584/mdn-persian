---
title: "CSSImportRule: media property"
short-title: media
slug: Web/API/CSSImportRule/media
page-type: web-api-instance-property
browser-compat: api.CSSImportRule.media
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`media`** از رابط {{domxref("CSSImportRule")}} یک شیء {{domxref("MediaList")}} برمی‌گرداند که فهرست رسانهٔ قاعدهٔ {{cssxref("@import")}} را نشان می‌دهد.

## مقدار

یک شیء {{domxref("MediaList")}}.

اگرچه خود ویژگی `media` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `MediaList` را جایگزین کنید، همچنان می‌توانید مستقیماً به ویژگی `media` مقدار بدهید که معادل مقدار دادن به ویژگی {{domxref("MediaList/mediaText", "mediaText")}} آن است. همچنین می‌توانید شیء `MediaList` را با استفاده از روش‌های {{domxref("MediaList/appendMedium", "appendMedium()")}} و {{domxref("MediaList/deleteMedium", "deleteMedium()")}} تغییر دهید.

## نمونه‌ها

### دریافت ویژگی media

استایل‌شیت زیر شامل یک قاعدهٔ {{cssxref("@import")}} است. بنابراین اولین مورد در فهرست قواعد CSS یک `CSSImportRule` خواهد بود. ویژگی `media` یک شیء {{domxref("MediaList")}} برمی‌گرداند که شامل ویژگی `mediaText` با مقدار `screen` است.

```css
@import "style.css" screen;
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].media); // A MediaList
```

### تنظیم ویژگی media

برای تغییر ویژگی `media` استایل‌شیت مرتبط، مقدار `media` را روی رشته‌ای شامل مقدار جدید قرار دهید.

```js
const myRules = document.styleSheets[0].cssRules;
myRules[0].media = "print";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}