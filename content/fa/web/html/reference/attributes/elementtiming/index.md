---
title: "elementtiming HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/elementtiming"
translated_by: "n8n + AI"
---

# ویژگی HTML `elementtiming`

ویژگی (attribute) **`elementtiming`** برای این استفاده می‌شود که مشخص کند یک عنصر برای رد‌یابی توسط اشیاء `PerformanceObserver` با نوع `"element"` علامت‌گذاری شده است. برای جزئیات بیشتر، به رابط `PerformanceElementTiming` مراجعه کنید.

این ویژگی می‌تواند روی عناصر `<img>`، عناصر `<image>` داخل یک `<svg>`، تصاویر پوستر (poster) عناصر `<video>`، عناصری که `background-image` دارند، و عناصری که حاوی گره‌های متنی (text nodes) هستند، مانند `<p>`، اعمال شود.

در DOM، این ویژگی به صورت `Element.elementTiming` بازتاب می‌شود.

## نکات استفاده

مقداری که برای `elementtiming` داده می‌شود، به عنوان شناسه‌ای برای عنصر مورد مشاهده عمل می‌کند.

```html
<img alt="alt" src="img.jpg" elementtiming="label for element" />
```

گزینه‌های خوب برای عناصری که ممکن است بخواهید مشاهده کنید عبارت‌اند از:

- تصویر اصلی یک مقاله.
- عنوان یک پست وبلاگ.
- تصاویر درون یک کاروسل (carousel) برای سایت فروشگاهی.
- تصویر پوستر ویدیوی اصلی یک صفحه.

## مثال‌ها

```html
<img
  alt="Alt for a main blog post image"
  src="my-massive-image.jpg"
  elementtiming="Main image" />

<p elementtiming="important-text">Some very important information.</p>
```

## همچنین ببینید

- `PerformanceElementTiming`
- `Element.elementTiming`