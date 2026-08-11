---
title: "Using HTML comments <!-- … -->"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Comments"
translated_by: "n8n + AI"
---

کامنت HTML (HTML comment) برای افزودن یادداشت‌های توضیحی به مارک‌آپ یا جلوگیری از تفسیر بخش‌هایی از سند توسط مرورگر استفاده می‌شود.

کامنت‌ها با رشته `<!--` شروع و با رشته `-->` ختم می‌شوند، معمولاً با متنی بین آن‌ها. این متن نمی‌تواند با `>` یا `->` شروع شود، نمی‌تواند حاوی `-->` یا `--!>` باشد، و نباید با `<!-` ختم شود، هرچند `<!` مجاز است.

مرورگر هنگام رندر کردن کد، کامنت‌ها را نادیده می‌گیرد. به عبارت دیگر، آن‌ها در صفحه نمایش داده نمی‌شوند - فقط در کد دیده می‌شوند. کامنت‌های HTML روشی برای نوشتن یادداشت‌های مفید درباره کد یا منطق برنامه هستند.

همین موضوع برای کامنت‌های [XML](/en-US/docs/Web/XML) نیز صادق است. علاوه بر این، در XML، مانند مارک‌آپ [SVG](/en-US/docs/Web/SVG) یا [MathML](/en-US/docs/Web/MathML)، یک کامنت نمی‌تواند شامل دنباله کاراکتری `--` باشد.

کامنت‌ها می‌توانند در یک خط یا چند خط استفاده شوند. می‌توان از آن‌ها در مکان‌های زیر استفاده کرد:

- قبل و بعد از Doctype
- قبل و بعد از عنصر `<html>`
- به عنوان محتوای بیشتر عناصر به جز: `<script>`، `<style>`، `<title>`، `<textarea>`، زیرا این عناصر محتوای خود را به عنوان متن خام (raw text) تفسیر می‌کنند.

> [!NOTE]
> هرچند عناصر `<script>` نباید دارای کامنت HTML باشند و باید به جای آن از [کامنت‌های جاوااسکریپت](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#comments) استفاده کنند، یک روش قدیمی وجود داشت که کل محتوای اسکریپت را در یک کامنت HTML قرار می‌دادند تا مرورگرهای قدیمی که جاوااسکریپت را پشتیبانی نمی‌کنند، آن را به صورت متن نمایش ندهند. این اکنون یک [ویژگی منسوخ خود جاوااسکریپت](/en-US/docs/Web/JavaScript/Reference/Deprecated_and_obsolete_features#html_comments) است و نباید به آن تکیه کنید.

## Syntax

```html
<!-- Comment -->
```

## Examples

```html
<!-- A one-line comment -->

<!--
A comment
that stretches
over several
lines
-->

<!-- The comment below disables
   the HTML contained within -->
<!--
<p>
   This content will not be rendered.
</p>
-->
```

## Notes

کامنت‌های HTML فقط به عنوان محتوا مجاز هستند. نمی‌توانید از آن‌ها درون یک تگ، مثلاً قبل از یک attribute HTML استفاده کنید.

مثل بیشتر زبان‌های برنامه‌نویسی که از syntax کامنت `<!-- -->` استفاده می‌کنند، کامنت‌ها نمی‌توانند تو در تو (nested) باشند. به عبارت دیگر، اولین نمونه `-->` که بعد از یک `<!--` می‌آید، کامنت را می‌بندد.

اگرچه کامنت‌ها با `<` شروع و با `>` ختم می‌شوند، اما کامنت یک عنصر HTML نیست.

## See also

- [Comments in JavaScript](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#comments)
- [Comments in CSS](/en-US/docs/Web/CSS/Guides/Syntax/Comments)
- API `Comment` (اینترفیس `Comment` از `Node` ارث‌بری می‌کند)