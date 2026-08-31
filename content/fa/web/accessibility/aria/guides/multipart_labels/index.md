---
title: "Multipart labels: Using ARIA for labels with embedded fields inside them"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Guides/Multipart_labels"
translated_by: "n8n + AI"
---
---
title: "Multipart labels: Using ARIA for labels with embedded fields inside them"
short-title: Using ARIA for labels with embedded fields
slug: Web/Accessibility/ARIA/Guides/Multipart_labels
page-type: guide
sidebar: accessibilitysidebar
---

## مشکل

فرمی دارید که در آن از کاربر سوالی می‌پرسید، اما پاسخ در خود سوال ذکر شده است. یک مثال کلاسیک که همه از تنظیمات مرورگر خود می‌شناسیم، تنظیم «حذف تاریخچه بعد از x روز» است. «حذف تاریخچه بعد از» در سمت چپ کادر متن قرار دارد، x عددی است مانند ۲۱، و کلمه «روز» بعد از کادر متن می‌آید و جمله‌ای را تشکیل می‌دهد که به راحتی قابل درک است.

اگر از صفحه‌خوان استفاده می‌کنید، آیا توجه کرده‌اید که وقتی به این تنظیم در فایرفاکس می‌روید، به شما می‌گوید «حذف تاریخچه بعد از ۲۱ روز»؟ و سپس اعلام می‌کند که در یک کادر متن هستید و عدد ۲۱ در آن وجود دارد. جالب نیست؟ نیازی نیست برای پیدا کردن واحد، پیمایش کنید. «روز» به راحتی می‌توانست «ماه» یا «سال» باشد، و در بسیاری از دیالوگ‌های معمولی، راهی برای فهمیدن این موضوع جز با پیمایش با دستورات مرور صفحه وجود ندارد.

راه‌حل در یک ویژگی ARIA به نام `aria-labelledby` است. پارامتر آن رشته‌ای است که شامل شناسه‌های عناصر HTML است که می‌خواهید در یک نام قابل دسترس واحد ترکیب کنید.

هم `aria-labelledby` و هم `aria-describedby` روی عنصر فرمی که باید برچسب‌گذاری شود، مشخص می‌شوند، به عنوان مثال یک `<input>`. در هر دو مورد، اتصالات برچسب/کنترل که ممکن است وجود داشته باشند، توسط `aria-labelledby` نادیده گرفته می‌شوند. اگر در یک صفحه HTML `aria-labelledby` ارائه می‌دهید، باید یک ساختار برچسب نیز برای پشتیبانی از مرورگرهای قدیمی‌تر که هنوز از ARIA پشتیبانی نمی‌کنند، ارائه دهید. با فایرفاکس ۳، کاربران کم‌بینا به طور خودکار قابلیت دسترسی بهتری از ویژگی جدید دریافت می‌کنند، اما کاربران مرورگرهای قدیمی‌تر نیز به این ترتیب در تاریکی رها نمی‌شوند.

### مثال

{{ EmbedLiveSample("Example") }}

```css hidden
body {
  margin: 1rem;
}
```

```html
<input
  aria-labelledby="labelShutdown shutdownTime shutdownUnit"
  type="checkbox" />

<span id="labelShutdown">Shut down computer after</span>

<input
  aria-labelledby="labelShutdown shutdownTime shutdownUnit"
  id="shutdownTime"
  type="text"
  value="10" />

<span id="shutdownUnit"> minutes</span>
```

## نکته‌ای برای کاربران JAWS 8

JAWS 8.0 منطق خاص خود را برای یافتن برچسب‌ها دارد، که باعث می‌شود همیشه accessibleName کادر متن یک سند HTML را نادیده بگیرد. با JAWS 8، راهی برای مجبور کردن آن به پذیرش برچسب از مثال بالا پیدا نکرده‌ام. اما NVDA و Window-Eyes به خوبی این کار را انجام می‌دهند و Orca در لینوکس نیز مشکلی ندارد.

> [!NOTE]
> TBD: add more compatibility info

## آیا این کار بدون ARIA امکان‌پذیر است؟

یکی از اعضای انجمن، بن میلارد، در یک پست وبلاگی اشاره کرده است که [کنترل‌ها را می‌توان در برچسب‌ها جاسازی کرد، همانطور که در مثال بالا با HTML 4 نشان داده شده است](https://projectcerbera.com/blog/2008/03/#day24)، با جاسازی `<input>` درون `<label>`. با تشکر از این اطلاعات، بن! این بسیار مفید است و نشان می‌دهد که برخی از تکنیک‌هایی که سال‌ها در دسترس بوده‌اند، حتی از نظر کارشناسان نیز دور می‌مانند. این تکنیک در فایرفاکس کار می‌کند، اما در بسیاری از مرورگرهای دیگر، از جمله IE، در حال حاضر کار نمی‌کند. برای برچسب‌هایی با کنترل‌های فرم جاسازی شده، استفاده از `aria-labelledby` همچنان بهترین روش است.