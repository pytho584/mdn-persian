---
title: "<frame> HTML frame element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/frame"
translated_by: "n8n + AI"
---

عنصر `<frame>` در HTML ناحیه مشخصی را تعریف می‌کند که می‌توان یک سند HTML دیگر را در آن نمایش داد. یک `<frame>` باید درون یک `<frameset>` استفاده شود.

> **توجه:** این عنصر منسوخ (deprecated) شده است. استفاده از `<frame>` به دلیل مشکلات عملکرد و نبود دسترس‌پذیری برای کاربران screen reader توصیه نمی‌شود. به جای آن بهتر است از `<iframe>` استفاده کنید.

## ویژگی‌ها (Attributes)

مانند همه عناصر HTML دیگر، این عنصر از [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

تمامی attributeهای این عنصر منسوخ (deprecated) و غیراستاندارد (non-standard) هستند.

- `src`
  - : این attribute مشخص می‌کند که کدام سند در frame نمایش داده شود.
- `name`
  - : این attribute برای نام‌گذاری frameها استفاده می‌شود. بدون نام‌گذاری، هر لینک در همان frame که در آن قرار دارد باز می‌شود — یعنی نزدیک‌ترین parent frame. برای اطلاعات بیشتر به [attribute `target`](/en-US/docs/Web/HTML/Reference/Elements/a#target) مراجعه کنید.
- `noresize`
  - : این attribute از تغییر اندازه frameها توسط کاربر جلوگیری می‌کند.
- `scrolling`
  - : این attribute وجود scrollbar را مشخص می‌کند. اگر استفاده نشود، مرورگر در صورت نیاز scrollbar اضافه می‌کند. دو گزینه وجود دارد: `"yes"` برای نمایش اجباری scrollbar حتی وقتی لازم نیست و `"no"` برای عدم نمایش آن حتی وقتی لازم است.
- `marginheight`
  - : این attribute ارتفاع حاشیه بین frameها را تعریف می‌کند.
- `marginwidth`
  - : این attribute عرض حاشیه بین frameها را تعریف می‌کند.
- `frameborder`
  - : این attribute به شما امکان می‌دهد border اطراف frame را مشخص کنید.

## مثال

### سند frameset

یک سند frameset به جای عنصر `<body>` از عنصر `<frameset>` استفاده می‌کند. عناصر `<frame>` داخل `<frameset>` قرار می‌گیرند.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <!-- Document metadata goes here -->
  </head>
  <frameset cols="400, 500">
    <frame src="https://developer.mozilla.org/en/HTML/Element/iframe" />
    <frame src="https://developer.mozilla.org/en/HTML/Element/frame" />
  </frameset>
</html>
```

اگر می‌خواهید صفحه HTML دیگری را درون `<body>` یک سند embed کنید، از عنصر `<iframe>` استفاده کنید.

## همچنین ببینید

- `<frameset>`
- `<iframe>`