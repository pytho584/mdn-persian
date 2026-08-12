---
title: <meta name="theme-color"> HTML attribute value
source: >-
  https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/theme-color
translated_by: n8n + AI
---

# \<meta name="theme-color"> HTML attribute value

مقدار **`theme-color`** برای ویژگی [`name`](../../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/meta/name/) المان \{{htmlelement("meta")\}}، رنگی را پیشنهاد می‌کند که مرورگرها باید برای سفارشی‌سازی نمایش صفحه یا رابط کاربری اطراف آن استفاده کنند. اگر مشخص شود، می‌توانید رنگ تم را با استفاده از ویژگی [`content`](../../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/meta/#content) در المان `<meta>` به عنوان یک مقدار CSS \{{cssxref("\<color>")\}} تعریف کنید.

برای مثال، برای نشان دادن اینکه یک سند باید از `cornflowerblue` به عنوان رنگ تم استفاده کند، المان `<meta>` را به این صورت تنظیم کنید:

```html
<meta name="theme-color" content="cornflowerblue" />
```

برای تنظیم media (رسانه)ای که فراداده‌ی رنگ تم به آن اعمال می‌شود، ویژگی [`media`](../../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/meta/#media) را با یک لیست media query معتبر اضافه کنید (به [مثال استفاده از media query با theme-color](index.md#using_a_media_query_with_theme-color) مراجعه کنید).

### نکات استفاده

یک المان `<meta name="theme-color">` ویژگی‌های اضافی زیر را دارد:

* [`content`](../../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/meta/#content)
  * : یک المان `<meta>` با `name=theme-color` باید دارای ویژگی `content` باشد که رنگ تم را تعریف کند. مقدار ویژگی `content` به صورت زیر است:
    * مقدار \{{cssxref("\<color>")\}}
      * : یک مقدار رنگ معتبر، مانند hexadecimal، RGB، نام رنگ و غیره.
* `media` \{{optional\_inline\}}
  * : هر نوع یا query رسانه‌ای معتبر. اگر ارائه شود، گزینه‌های رنگ تم سند که در ویژگی `content` تعریف شده‌اند، زمانی که media query مطابقت داشته باشد، به مرورگر پیشنهاد می‌شوند.

### مثال‌ها

#### تنظیم یک مقدار رنگ

کد زیر را در نظر بگیرید که از `<meta>` برای تنظیم یک رنگ تم استفاده می‌کند:

```html
<meta name="theme-color" content="#4285f4" />
```

تصویر زیر اثر این تنظیم را در Chrome روی دستگاه موبایل Android نشان می‌دهد:

_اعتبار تصویر: از_ [_Icons & Browser Colors_](https://web.dev/articles/icons-and-browser-colors)_، ساخته و به اشتراک‌گذاری شده توسط Google و استفاده شده با شرایط مجوز_ [_Creative Commons 4.0 Attribution License_](https://creativecommons.org/licenses/by/4.0/)_._

#### استفاده از media query با `theme-color`

می‌توانید یک نوع یا query رسانه‌ای را درون ویژگی [`media`](../../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/meta/#media) قرار دهید. در این صورت `theme-color` فقط زمانی تنظیم می‌شود که شرط media برقرار باشد. برای مثال:

```html
<meta
  name="theme-color"
  content="cornflowerblue"
  media="(prefers-color-scheme: light)" />
<meta
  name="theme-color"
  content="dimgray"
  media="(prefers-color-scheme: dark)" />
```

### مشخصات

### سازگاری با مرورگرها

### همچنین ببینید

* مقدار `name` در `<meta>` برای [`color-scheme`](../../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/meta/name/color-scheme/)
* ویژگی CSS \{{cssxref("color-scheme")\}}
* media query \{{cssxref("@media/prefers-color-scheme")\}}
