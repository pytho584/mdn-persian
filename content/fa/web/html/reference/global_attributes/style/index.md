---
title: "style HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/style"
translated_by: "n8n + AI"
---

## ویژگی سراسری `style`

ویژگی سراسری **`style`** حاوی اعلان‌های استایل [CSS](/en-US/docs/Web/CSS) است که روی عنصر اعمال می‌شوند. توجه داشته باشید که توصیه می‌شود استایل‌ها در یک یا چند فایل جداگانه تعریف شوند. این ویژگی و عنصر `<style>` عمدتاً برای استایل‌دهی سریع، مثلاً برای اهداف آزمایشی، به کار می‌روند.

```html interactive-example
<div style="background: #ffe7e8; border: 2px solid #e66465">
  <p style="margin: 15px; line-height: 1.5; text-align: center">
    Well, I am the slime from your video<br />
    Oozin' along on your livin' room floor.
  </p>
</div>
```

> [!NOTE]
> از این ویژگی نباید برای انتقال اطلاعات معنایی استفاده شود. حتی اگر همه استایل‌ها حذف شوند، صفحه باید از نظر معنایی صحیح باقی بماند. معمولاً نباید برای پنهان کردن اطلاعات نامرتبط به کار رود؛ این کار باید با ویژگی `hidden` انجام شود.

## همچنین ببینید

- [Global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- [HTMLElement.style](/en-US/docs/Web/API/HTMLElement/style)