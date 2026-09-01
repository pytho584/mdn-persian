---
title: "HTMLMetaElement: media property"
short-title: media
slug: Web/API/HTMLMetaElement/media
page-type: web-api-instance-property
browser-compat: api.HTMLMetaElement.media
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMetaElement.media`** امکان تعیین رسانه (media) برای فرادادهٔ `theme-color` را فراهم می‌کند.

ویژگی `theme-color` امکان تعیین رنگ نوار ابزار یا رابط کاربری مرورگر را در مرورگرها و سیستم‌عامل‌هایی که از این ویژگی پشتیبانی می‌کنند، می‌دهد.
ویژگی `media` امکان تعیین رنگ‌های تم متفاوت برای مقادیر مختلف `media` را فراهم می‌کند.

## مقدار

یک رشته (String).

## مثال‌ها

### تنظیم رنگ تم برای حالت تیره

مثال زیر یک عنصر جدید `<meta>` با ویژگی `name` تنظیم‌شده روی [`theme-color`](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification) ایجاد می‌کند.
ویژگی `content` روی `#3c790a`، ویژگی `media` روی `prefers-color-scheme: dark` تنظیم می‌شود و عنصر به `<head>` سند اضافه می‌گردد.
وقتی کاربر حالت تیره را در سیستم‌عامل خود مشخص کرده باشد، می‌توان از ویژگی `media` برای تعیین یک `theme-color` متفاوت استفاده کرد:

```js
const meta = document.createElement("meta");
meta.name = "theme-color";
meta.content = "#3c790a";
meta.media = "(prefers-color-scheme: dark)";
document.head.appendChild(meta);
```

### تنظیم رنگ‌های تم بر اساس اندازه دستگاه

بیشتر ویژگی‌های متا فقط یک‌بار قابل استفاده هستند. با این حال، `theme-color` را می‌توان چندین بار استفاده کرد، به شرط آنکه مقادیر `media` منحصربه‌فرد ارائه شوند.

این مثال دو عنصر متا با `theme-color` اضافه می‌کند؛ یکی برای همه دستگاه‌ها و دیگری برای صفحه‌نمایش‌های کوچک.
ترتیب تطبیق Media Query مهم است، بنابراین کوئری خاص‌تر باید دیرتر در سند اضافه شود، همان‌طور که در زیر نشان داده شده است:

```js
// افزودن رنگ تم برای همه دستگاه‌ها
const meta1 = document.createElement("meta");
meta1.name = "theme-color";
meta1.content = "white";
document.head.appendChild(meta1);

// افزودن رنگ تم برای دستگاه‌های کوچک
const meta2 = document.createElement("meta");
meta2.name = "theme-color";
meta2.media = "(width <= 600px)";
meta2.content = "black";
document.head.appendChild(meta2);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meta")}}
- [مقادیر ممکن برای Media Queryها](/en-US/docs/Web/CSS/Guides/Media_queries/Using)