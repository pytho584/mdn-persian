---
title: "ARIA: comment role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/comment_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: comment role"
short-title: comment
slug: Web/Accessibility/ARIA/Reference/Roles/comment_role
page-type: aria-role
sidebar: accessibilitysidebar
---

نقش `comment` به‌طور معنایی یک دیدگاه/واکنش به برخی محتوا در صفحه، یا به یک دیدگاه قبلی را نشان می‌دهد.

> [!NOTE]
> نقش comment در WAI-ARIA 1.3 ([آخرین پیش‌نویس ARIA](https://w3c.github.io/aria/)) پیشنهاد شده است که همچنان در حال تدوین است.

## مثال‌ها

در مثال زیر، یک بخش از سند داریم که بر روی آن دیدگاه ثبت شده است. بخش دارای دیدگاه با استفاده از `<span role="mark">` نشانه‌گذاری شده است.

دیدگاه مربوطه با استفاده از یک ساختار HTML که در یک `<div>` با `role="comment"` قرار گرفته، نشانه‌گذاری شده است.

```html
<p>
  The last half of the song is a slow-rising crescendo that peaks at the
  <span role="mark" aria-details="thread-1">end of the guitar solo</span>,
  before fading away sharply.
</p>

<div role="comment" id="thread-1" data-author="chris">
  <h3>Chris said</h3>
  <p class="comment-text">I really think this moment could use more cowbell.</p>
  <p><time datetime="2019-03-30T19:29">March 30 2019, 19:29</time></p>
</div>
```

برای关联 کردن دیدگاه با متنی که بر روی آن دیدگاه ثبت شده، باید متن دارای دیدگاه را با عنصری که ویژگی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) را دارد بپیچیم؛ مقدار این ویژگی باید شناسه (ID) دیدگاه باشد.

### چند دیدگاه

از آنجا که `aria-details` اکنون می‌تواند چندین شناسه را بپذیرد، می‌توانیم چند دیدگاه را با همان حاشیه‌نویسی مرتبط کنیم، مانند زیر:

```html
<p>
  The last half of the song is a slow-rising crescendo that peaks at the
  <mark aria-details="thread-1 thread-2">end of the guitar solo</mark>, before
  fading away sharply.
</p>

<div role="comment" id="thread-1" data-author="chris">
  <h3>Chris said</h3>
  <p class="comment-text">I really think this moment could use more cowbell.</p>
  <p><time datetime="2019-03-30T19:29">March 30 2019, 19:29</time></p>
</div>

<div role="comment" id="thread-2" data-author="chris">
  <h3>Marcus said</h3>
  <p class="comment-text">
    The guitar solo could do with a touch more chorus, and a slightly lower
    volume.
  </p>
  <p><time datetime="2019-03-29T15:35">March 29 2019, 15:35</time></p>
</div>
```

### دیدگاه‌های تودرتو

امکان تودرتو کردن دیدگاه‌ها در یکدیگر وجود دارد، مانند زیر:

```html
<div role="comment" id="thread-1" data-author="chris">
  <h3>Chris said</h3>
  <p class="comment-text">I really think this moment could use more cowbell.</p>
  <p><time datetime="2021-03-30T19:29">March 30 2021, 19:29</time></p>

  <div role="comment" data-author="marcus">
    <h3>Marcus replied</h3>
    <p class="comment-text">
      I don't know about that. I think the cowbell could distract from the solo.
    </p>
    <p><time datetime="2021-03-30T21:02">March 30 2021, 21:02</time></p>
  </div>
</div>
```

## نگرانی‌های دسترس‌پذیری

هیچ‌کدام.

## مشخصات

بخشی از WAI-ARIA 1.3 خواهد بود که همچنان در حال تدوین است.