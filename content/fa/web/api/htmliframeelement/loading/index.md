---
title: "HTMLIFrameElement: loading property"
short-title: loading
slug: Web/API/HTMLIFrameElement/loading
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.loading
---

{{APIRef("HTML DOM")}}

ویژگی **`loading`** از رابط {{domxref("HTMLIFrameElement")}} یک رشته است که به مرورگر راهنمایی می‌کند که آیا [iframe](/en-US/docs/Web/HTML/Reference/Elements/iframe) باید بلافاصله هنگام بارگذاری صفحه بارگذاری شود یا فقط زمانی که به آن نیاز است.

از این ویژگی می‌توان برای بهینه‌سازی بارگذاری محتویات سند استفاده کرد.
iframeهایی که هنگام بارگذاری صفحه دیده می‌شوند می‌توانند فوراً (به‌صورت eager) دانلود شوند، در حالی که iframeهایی که احتمالاً در بارگذاری اولیه صفحه خارج از دید هستند می‌توانند به‌صورت تنبل (lazy) دانلود شوند — درست قبل از اینکه در {{Glossary("visual viewport")}} پنجره ظاهر شوند.

## مقدار

رشته‌ای که به عامل کاربر راهنمایی می‌کند که چگونه بارگذاری iframe را به بهترین شکل زمان‌بندی کند.
مقادیر ممکن عبارت‌اند از:

- `eager`
  - : به محض پردازش عنصر، iframe را بارگذاری کن.
    این مقدار پیش‌فرض است.
- `lazy`
  - : وقتی مرورگر تشخیص دهد که احتمالاً در آینده نزدیک به iframe نیاز خواهد بود، آن را بارگذاری کن.

## نکات استفاده

### جاوااسکریپت باید فعال باشد

بارگذاری فقط زمانی به تأخیر می‌افتد که جاوااسکریپت فعال باشد، صرف‌نظر از مقدار این ویژگی.

این یک اقدام ضد ردیابی است، زیرا اگر عامل کاربر در حالی که اسکریپت‌ها غیرفعال هستند از بارگذاری تنبل پشتیبانی کند، همچنان ممکن است سایتی بتواند موقعیت تقریبی اسکرول کاربر را در طول یک نشست ردیابی کند؛ با قرار دادن استراتژیک iframeها در نشانه‌گذاری صفحه به‌گونه‌ای که سرور بتواند تعداد و زمان درخواست‌های آن‌ها را پیگیری کند.

### زمان‌بندی رویداد load

رویداد {{domxref("Window.load_event", "load")}} هنگامی رخ می‌دهد که سند به‌طور کامل پردازش شده باشد.

iframeهای بارگذاری‌شده به‌صورت تنبل، حتی اگر در دیدگاه بصری (visual viewport) باشند و بنابراین هنگام بارگذاری صفحه واکشی شوند، بر زمان‌بندی رویداد `load` تأثیری ندارند.
همه iframeهای بارگذاری‌شده به‌صورت eager در سند باید قبل از اینکه رویداد `load` رخ دهد واکشی شده باشند.

## مثال‌ها

### استفاده پایه

مثال زیر نشان می‌دهد که چگونه می‌توانید یک iframe با بارگذاری تنبل تعریف کنید و سپس آن را به یک `<div>` در سند اضافه کنید.
این قاب فقط زمانی بارگذاری می‌شود که در شرف ظاهر شدن باشد.

```js
// Define iframe with lazy loading
const iframe = document.createElement("iframe");
iframe.src = "https://example.com";
iframe.width = 320;
iframe.height = 240;
iframe.loading = "lazy";

// Add to div element with class named frameDiv
const frameDiv = document.querySelector("div.frameDiv");
frameDiv.appendChild(iframe);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("iframe")}}
- [یادگیری: کارایی وب](/en-US/docs/Learn_web_development/Extensions/Performance)
- [بارگذاری تنبل](/en-US/docs/Web/Performance/Guides/Lazy_loading) در راهنمای کارایی وب MDN
- [وقت آن رسیده که iframeهای خارج از صفحه را با بارگذاری تنبل بارگذاری کنیم!](https://web.dev/articles/iframe-lazy-loading) در web.dev