---
title: "ARIA: aria-brailleroledescription attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-brailleroledescription attribute"
short-title: aria-brailleroledescription
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-brailleroledescription
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-brailleroledescription` توصیفی کوتاه و قابل‌خواندن برای انسان و بومی‌شده توسط نویسنده، از نقش یک عنصر تعریف می‌کند که قرار است به بریل تبدیل شود.

## توضیحات

بریل ترانویسی یک‌به‌یک از حروف و اعداد نیست؛ بلکه شامل اختصارها، ترکیب‌های کوتاه و کاراکترهایی است که واژه‌ها را نشان می‌دهند (که لوگوگرام نامیده می‌شوند).

به‌جای تبدیل توصیف‌های طولانی نقش به بریل، ویژگی `aria-brailleroledescription` امکان ارائه یک نسخه کوتاه‌شده از مقدار [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) را فراهم می‌کند؛ که توصیفی قابل‌خواندن برای انسان، بومی‌شده توسط نویسنده، برای نقش یک عنصر است، تا تجربه کاربری با رابط‌های بریل بهبود یابد.

در واقع، مقدار `aria-brailleroledescription` نسخه کوتاه‌شده از ویژگی `aria-roledescription` است که قرار است به بریل تبدیل شود.

```html
<article
  aria-roledescription="slide"
  aria-brailleroledescription="sld"
  aria-labelledby="slide1heading">
  <h1 id="slide1heading">Welcome to my talk</h1>
  <img alt="Me" src="images/me.jpg" />
</article>
```

بیشتر فناوری‌های کمکی، مانند صفحه‌خوان‌ها، متن بالا را به‌صورت «slide, welcome to my talk. Image, Me.» می‌خوانند. فناوری‌های کمکی بریل، آن را به‌صورت «sld welcome to my talk gra me» در بریل ارائه خواهند داد. به عنصر معنایی {{HTMLElement('article')}} با ویژگی `aria-roledescription` نقش «slide» داده شده است؛ «slide» نقشی است که در مشخصات تعریف نشده، اما نقش رایجی برای اسلایدها در یک ارائه است. در بریل، این نقش به‌صورت «sld» ارائه می‌شود. «gra» مخفف «graphic» است و به این صورت نقش «image» در بریل کوتاه شده است.

ویژگی `aria-brailleroledescription` فقط باید برای روشن کردن هدف نقش‌های ظرف غیرتعاملی مانند «group» یا «region» استفاده شود، یا برای ارائه توصیف دقیق‌تری از یک ویجت در بافت بریل به کار رود.

از آنجا که ویژگی `aria-brailleroledescription` نحوه بومی‌سازی و بیان نام یک نقش را توسط فناوری‌های کمکی در بریل بازنویسی می‌کند، مقادیر نامناسب مانع درک و تعامل کاربران با یک عنصر در رابط‌های بریل خواهد شد.

فقط زمانی از `aria-brailleroledescription` استفاده کنید که [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) وجود داشته باشد. با این حال، اگر مقدار `aria-roledescription` در بریل کارآمد است، نسخه بریل این ویژگی ضروری نیست. به‌طور کلی، `aria-brailleroledescription` فقط باید در موارد نادری استفاده شود که `aria-roledescription` برای بریل بیش از حد طولانی است.

چند قانون که باید به خاطر بسپارید:

- فقط `aria-brailleroledescription` را روی عناصری اعمال کنید که نقش ARIA معتبر دارند یا عناصری با معناشناسی نقش ضمنی.
- ویژگی `aria-brailleroledescription`، در صورت وجود، باید مقداری غیر خالی و غیر null داشته باشد که با مقدار `aria-roledescription` متفاوت باشد؛ و آن نیز باید با نقش صریح یا نقش معنایی ضمنی ARIA متفاوت باشد.
- از استفاده از الگوهای بریل یونیکد خودداری کنید. اگر استفاده از آنها ضروری است، اطمینان حاصل کنید که مقدار `aria-brailleroledescription` حاوی محتوایی به‌جز الگوهای بریل یونیکد، فاصله‌های خالی و الگوی بریل dots-0 باشد.
- اطمینان حاصل کنید که مقدار همیشه به زبان سند بومی‌شده است.

> [!WARNING]
> اگر محتوا فقط شامل الگوهای بریل یونیکد باشد، مقدار بر اساس جدول ترجمه موردعلاقه کاربر ترجمه نخواهد شد.

> [!NOTE]
> از `aria-brailleroledescription` برای تکرار `aria-roledescription` استفاده نکنید. این ویژگی را فقط زمانی اضافه کنید که `aria-roledescription` بازنمایی بریل مناسبی ارائه نمی‌دهد.

مقدار `aria-brailleroledescription` در موارد زیر در اختیار کاربر بریل قرار نخواهد گرفت:

- مقدار خالی باشد، یا فقط شامل کاراکترهای فاصله یا الگوی بریل خالی: dots-0 (U+2800) باشد.
- عنصری که ویژگی به آن اعمال شده دارای نقش صریح یا ضمنی WAI-ARIA باشد که `aria-brailleroledescription` در آن ممنوع است، از جمله نقش `generic`.
- عنصری که ویژگی به آن اعمال شده، `aria-roledescription` معتبر نداشته باشد.

> [!NOTE]
> سایت‌ها و برنامه‌های خود را با کاربران روزمره فناوری‌های کمکی، از جمله خوانندگان بریل، آزمایش کنید تا مطمئن شوید محتوایتان در بریل معنادار است.

## مقادیر

- `<string>`
  - : مقدار یک رشته است، یک نوع مقدار بدون قید، که قرار است به بریل تبدیل شود.

## نقش‌های مرتبط

در **همه** نقش‌ها (به‌جز [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role)) استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- {{domxref("Element.ariaBrailleRoleDescription")}}
- [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription).
- [`Element.ariaRoleDescription`](/en-US/docs/Web/API/Element/ariaRoleDescription)