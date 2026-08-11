---
title: "crossorigin HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/crossorigin"
translated_by: "n8n + AI"
---

# ویژگی HTML `crossorigin`

ویژگی **`crossorigin`** روی المان‌های `<audio>`، `<img>`، `<link>`، `<script>` و `<video>` معتبر است. این ویژگی پشتیبانی از [CORS](/en-US/docs/Web/HTTP/Guides/CORS) را فراهم می‌کند و نحوهٔ مدیریت درخواست‌های cross-origin توسط المان را مشخص می‌کند. به این ترتیب امکان پیکربندی درخواست‌های CORS برای داده‌های دریافت‌شده توسط المان فراهم می‌شود. بسته به نوع المان، این ویژگی می‌تواند یک ویژگی تنظیمات CORS (CORS settings attribute) باشد.

ویژگی محتوایی `crossorigin` در المان‌های رسانه‌ای (media) یک ویژگی تنظیمات CORS است.

این ویژگی‌ها از نوع [شمارشی (enumerated)](https://developer.mozilla.org/en-US/docs/Glossary/Enumerated) هستند و مقادیر ممکن زیر را دارند:

- `anonymous`
  - درخواست از هدرهای CORS استفاده می‌کند و فلگ credentials روی `'same-origin'` تنظیم می‌شود. هیچ **اعتبارنامهٔ کاربری** از طریق کوکی‌ها، گواهی‌های TLS سمت کلاینت یا احراز هویت HTTP رد و بدل نمی‌شود، مگر اینکه مقصد همان origin باشد.
- `use-credentials`
  - درخواست از هدرهای CORS استفاده می‌کند، فلگ credentials روی `'include'` تنظیم می‌شود و **اعتبارنامه‌های کاربر** همیشه ارسال می‌شوند.
- `""`
  - تنظیم نام ویژگی به مقدار خالی، مثلاً `crossorigin` یا `crossorigin=""`، همان `anonymous` محسوب می‌شود.

یک کلیدواژهٔ نامعتبر و یک رشتهٔ خالی به‌عنوان کلیدواژهٔ `anonymous` رفتار می‌شوند.

به‌طور پیش‌فرض (یعنی وقتی ویژگی مشخص نشده باشد)، اصلاً از CORS استفاده نمی‌شود. عامل کاربر (user agent) اجازهٔ دسترسی کامل به منبع را درخواست نمی‌کند و در مورد درخواست cross-origin، محدودیت‌های خاصی بر اساس نوع المان اعمال می‌شود:

| المان | محدودیت‌ها |
| --- | --- |
| `img`، `audio`، `video` | وقتی منبع در `<canvas>` قرار می‌گیرد، المان به‌عنوان [آلوده (tainted)](https://developer.mozilla.org/en-US/docs/Web/HTML/How_to/CORS_enabled_image#security_and_tainted_canvases) علامت‌گذاری می‌شود. |
| `script` | دسترسی به ثبت خطا از طریق `window.onerror` محدود خواهد شد. |
| `link` | درخواست بدون هدر `crossorigin` مناسب ممکن است رد شود. |

> **نکته:** ویژگی `crossorigin` برای `rel="icon"` در مرورگرهای مبتنی بر Chromium پشتیبانی نمی‌شود. به [issue مربوطه در Chromium](https://crbug.com/1121645) مراجعه کنید.

## مثال‌ها

### استفاده از `crossorigin` با المان `<script>`

می‌توانید از المان `<script>` زیر استفاده کنید تا به مرورگر بگویید اسکریپت `https://example.com/example-framework.js` را بدون ارسال اعتبارنامه‌های کاربر اجرا کند.

```html
<script
  src="https://example.com/example-framework.js"
  crossorigin="anonymous"></script>
```

### Web manifest با اعتبارنامه

هنگام دریافت [manifest](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest) که به اعتبارنامه نیاز دارد، باید از مقدار `use-credentials` استفاده شود، حتی اگر فایل از همان origin باشد.

```html
<link rel="manifest" href="/app.webmanifest" crossorigin="use-credentials" />
```

## همچنین ببینید

- [Cross-Origin Resource Sharing (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [ویژگی HTML: `rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel)