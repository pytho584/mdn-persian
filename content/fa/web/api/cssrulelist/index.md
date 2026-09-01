---
title: "CSSRuleList"
slug: Web/API/CSSRuleList
page-type: web-api-interface
browser-compat: api.CSSRuleList
---

{{ APIRef("CSSOM") }}

یک `CSSRuleList` مجموعهای مرتب از اشیاء {{domxref("CSSRule")}} فقط‌خواندنی را نشان می‌دهد.

با اینکه شیء `CSSRuleList` فقط‌خواندنی است و نمی‌توان آن را مستقیماً تغییر داد، به‌عنوان یک شیءِ `live` (زنده) در نظر گرفته می‌شود؛ زیرا محتوای آن می‌تواند در طول زمان تغییر کند.

برای ویرایش قواعد زیربنایی که توسط اشیاء `CSSRule` بازگردانده می‌شوند، از {{domxref("CSSStyleSheet.insertRule()")}} و {{domxref("CSSStyleSheet.deleteRule()")}} استفاده کنید که متدهایی از {{domxref("CSSStyleSheet")}} هستند.

این رابط [تلاشی برای ایجاد فهرستی غیرقابل‌تغییر](https://stackoverflow.com/questions/74630989/why-use-domstringlist-rather-than-an-array/74641156#74641156) بود و تنها به این دلیل همچنان پشتیبانی می‌شود که کدهایی که قبلاً از آن استفاده می‌کنند، خراب نشوند. APIهای مدرن ساختارهای فهرستی را با استفاده از نوع‌هایی مبتنی بر [آرایه‌های](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) جاوااسکریپت نمایش می‌دهند؛ بدین ترتیب بسیاری از متدهای آرایه در دسترس قرار می‌گیرند و در عین حال معناشناسی‌های اضافی نیز بر نحوهٔ استفاده تحمیل می‌شود (مانند فقط‌خواندنی کردن اقلام آن‌ها).

این دلایل تاریخی به این معنا نیست که شما به‌عنوان توسعه‌دهنده باید از `CSSRuleList` اجتناب کنید. شما خودتان اشیاء `CSSRuleList` را نمی‌سازید، بلکه آن‌ها را از APIهایی مانند {{domxref("CSSStyleSheet.cssRules")}} و {{domxref("CSSKeyframesRule.cssRules")}} دریافت می‌کنید و این APIها منسوخ نشده‌اند. با این حال، مراقب تفاوت‌های معنایی با یک آرایهٔ واقعی باشید.

## ویژگی‌های نمونه

- {{domxref("CSSRuleList.length")}} {{ReadOnlyInline}}
  - : یک عدد صحیح برمی‌گرداند که تعداد اشیاء {{domxref("CSSRule")}} را در مجموعه نشان می‌دهد.

## متدهای نمونه

- {{domxref("CSSRuleList.item()")}}
  - : یک {{domxref("CSSRule")}} را برمی‌گرداند.

## نمونه‌ها

در مثال زیر، یک شیوه‌نامه (stylesheet) با سه قاعده وجود دارد. استفاده از {{domxref("CSSStyleSheet.cssRules")}} یک `CSSRuleList` برمی‌گرداند که در کنسول چاپ می‌شود.

تعداد قواعد موجود در فهرست با استفاده از {{domxref("CSSRuleList.length")}} در کنسول چاپ می‌شود. اولین {{domxref("CSSRule")}} را می‌توان با استفاده از `0` به‌عنوان پارامتر برای {{domxref("CSSRuleList.item")}} بازگرداند؛ در این مثال، این کار قواعد تنظیم‌شده برای انتخابگر `body` را برمی‌گرداند.

### CSS

```css
body {
  font-family:
    system-ui,
    -apple-system,
    sans-serif;
  margin: 2em;
}

.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, 200px);
}

.container > * {
  background-color: #3740ff;
  color: white;
}
```

### JavaScript

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules);
console.log(myRules.length);
console.log(myRules[0]);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`CSSRule`](/en-US/docs/Web/API/CSSRule)