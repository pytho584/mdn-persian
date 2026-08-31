---
title: "ARIA: aria-description attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-description attribute"
short-title: aria-description
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-description
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-description
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-description` یک مقدار رشته‌ای را تعریف می‌کند که عنصر فعلی را توصیف یا حاشیه‌نویسی می‌کند.

> [!NOTE]
> `aria-description` همچنان در پیش‌نویس ویراستار W3C برای ARIA 1.3 قرار دارد. در حال حاضر، همچنان از [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) استفاده کنید که از ARIA 1.1 پشتیبانی می‌شود.

## توضیحات

ویژگی سراسری `aria-description` مکانیزمی را برای توسعه‌دهنده فراهم می‌کند تا عنصر فعلی را توصیف یا حاشیه‌نویسی کند و زمینه بهتری را برای کاربران فناوری کمکی فراهم آورد.

```html
<div
  role="application"
  aria-label="calendar"
  aria-description="Game schedule for the Boston Red Sox 2021 Season">
  <h1>Red Sox 2021</h1>
  <div role="grid">…</div>
</div>
```

ویژگی `aria-description` مشابه [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) است، زیرا هر دو یک رشته متنی را برای مرتبط‌سازی با عنصر فراهم می‌کنند، اما برچسب باید کوتاه و مختصر باشد، در حالی که توضیحات می‌تواند طولانی‌تر باشد، زیرا برای ارائه زمینه و اطلاعات بیشتر در نظر گرفته شده است.

ویژگی‌های `aria-description` و `aria-describedby` هدف یکسانی دارند؛ هر دو متن توصیفی اضافی را برای شیئی که روی آن تنظیم شده‌اند در اختیار کاربر قرار می‌دهند. اگر متن توصیفی در DOM موجود است، به جای آن از [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) استفاده کنید.

ویژگی `aria-description` فقط باید زمانی استفاده شود که ارائه یک توضیح قابل مشاهده تجربه کاربری مطلوبی نباشد. ویژگی `aria-describedby` به عنوان مقدار خود فهرستی از `id`های عناصری را می‌گیرد که حاوی متن توصیفی درباره شیء هستند. از `aria-description` زمانی استفاده می‌شود که متن توصیفی مناسبی وجود نداشته باشد که بتوان از طریق ارجاع `id` با شیء مرتبط کرد. اگر هر دو ویژگی وجود داشته باشند، `aria-describedby` در تعریف ویژگی {{glossary("accessible description")}} اولویت دارد.

محتوای توضیحات، چه توسط `aria-description` یا `aria-describedby` تنظیم شده باشد، باید متن ساده باشد. اگر محتوا بسیار طولانی است، نیازهای معنایی دارد، یا ساختار پیمایشی دارد، به جای آن از [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) استفاده کنید.

## مقادیر

- `<string>`
  - : مقدار یک رشته است، یک نوع مقدار بدون محدودیت، که قرار است به کاربر فناوری کمکی منتقل شود.

## رابط‌های مرتبط

- {{domxref("Element.ariaDescription")}}
  - : ویژگی [`ariaDescription`](/en-US/docs/Web/API/Element/ariaDescription)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-description` را منعکس می‌کند که یک مقدار رشته‌ای را تعریف می‌کند که عنصر فعلی را توصیف یا حاشیه‌نویسی می‌کند.

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ویژگی `title` در HTML](/en-US/docs/Web/HTML/Reference/Global_attributes/title)
- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
- [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details)