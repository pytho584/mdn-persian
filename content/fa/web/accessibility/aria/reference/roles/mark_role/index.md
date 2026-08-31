---
title: "ARIA: mark role"
short-title: mark
slug: Web/Accessibility/ARIA/Reference/Roles/mark_role
page-type: aria-role
sidebar: accessibilitysidebar
translated_by: "n8n + AI"
---

## ARIA: نقش نشان‌گذاری (mark)

نقش `mark` به محتوایی اشاره دارد که به دلیل اهمیت آن در زمینه‌ای که در آن قرار دارد، برای اهداف مرجع یا یادداشت‌برداری علامت‌گذاری یا برجسته شده است. این از نظر معنایی معادل عنصر HTML `<mark>` است. در صورت امکان، باید از این عنصر استفاده کنید.

کاربردهای مثال برای `mark` دقیقاً مشابه عنصر `<mark>` است. این کاربردها شامل برجسته‌کردن متنی در یک نقل‌قول است که مورد توجه ویژه است اما در منبع اصلی علامت‌گذاری نشده است، قابل قیاس با استفاده از ماژیک‌هایلایت برای علامت‌گذاری بخش‌های یک مقاله چاپی و نشان‌دادن بخش‌هایی از محتوا که با فعالیت فعلی کاربر مرتبط است، مانند برجسته‌کردن مطابقت‌های متنی یافت‌شده توسط یک ویژگی جستجو.

از `mark` برای سبک‌دهی صرفاً تزئینی مانند برجسته‌سازی نحو (syntax highlighting) استفاده نکنید.

عنصر `mark` نباید یک نام قابل دسترسی دریافت کند؛ هر دو ویژگی `aria-label` و `aria-labelledby` در `mark` ممنوع هستند.

## مثال‌ها

در مثال زیر یک بخش از سند داریم که نظرگذاری شده است. بخش نظرگذاری‌شده با استفاده از `<span role="mark">` نشانه‌گذاری شده است.

```html
<p>
  The last half of the song is a slow-rising crescendo that peaks at the
  <span role="mark" aria-details="thread-1">end of the guitar solo</span>,
  before fading away sharply.
</p>

<div role="comment" id="thread-1" data-author="chris">
  <h3>Chris said</h3>
  <p class="comment-text">I really think this moment could use more cowbell.</p>
  <p><time datetime="2022-03-30T19:29">March 30 2022, 19:29</time></p>
</div>
```

نظر مرتبط با استفاده از یک ساختار HTML که در یک `<div>` با [`role="comment"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/comment_role) پیچیده شده، نشانه‌گذاری شده است.

برای مرتبط‌سازی نظر با متنی که نظر روی آن داده شده، باید متن نظرگذاری‌شده را درون یک عنصر حاوی ویژگی `aria-details` قرار دهیم که مقدار آن باید شناسه (ID) نظر باشد.

## بهترین شیوه‌ها

### ترجیح HTML

استفاده از عنصر `<mark>` به طور خودکار اعلام می‌کند که یک گره دارای نقش `mark` است. در صورت امکان، ترجیح دهید از آن استفاده کنید.

## مشخصات

بخشی از [WAI-ARIA 1.3](https://w3c.github.io/aria/#mark) خواهد بود که هنوز در حال پیش‌نویس است.

## همچنین ببینید

- عنصر HTML `<mark>`