---
title: "<frameset> HTML frameset element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/frameset"
translated_by: "n8n + AI"
---

# عنصر `<frameset>` در HTML

عنصر **`<frameset>`** در [HTML](/en-US/docs/Web/HTML) برای نگهداری عناصر `<frame>` استفاده می‌شود.

> **نکته:** از آنجا که استفاده از قاب‌ها (Frames) منسوخ شده و به‌جای آن استفاده از `<iframe>` توصیه می‌شود، این عنصر معمولاً در وب‌سایت‌های مدرن به‌کار نمی‌رود.

## ویژگی‌ها (Attributes)

مانند سایر عناصر HTML، این عنصر از [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `cols` (منسوخ، غیراستاندارد)
  - : این ویژگی تعداد و اندازه فضاهای افقی (ستون‌ها) در یک frameset را مشخص می‌کند.
- `rows` (منسوخ، غیراستاندارد)
  - : این ویژگی تعداد و اندازه فضاهای عمودی (ردیف‌ها) در یک frameset را مشخص می‌کند.

## مثال

### یک سند Frameset

یک سند frameset به‌جای عنصر `<body>` دارای عنصر `<frameset>` است. عناصر `<frame>` داخل `<frameset>` قرار می‌گیرند.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <!-- Document metadata goes here -->
  </head>
  <frameset cols="50%, 50%">
    <frame
      src="https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/iframe" />
    <frame
      src="https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/frame" />
  </frameset>
</html>
```

اگر می‌خواهید صفحه HTML دیگری را داخل `<body>` سند جاسازی کنید، از عنصر `<iframe>` استفاده کنید.

## همچنین ببینید

- `<frame>`
- `<iframe>`