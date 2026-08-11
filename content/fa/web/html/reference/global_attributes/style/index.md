---
title: "style HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/style"
translated_by: "n8n + AI"
---

**`style`** یک [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) است که شامل اعلان‌های استایل [CSS](/en-US/docs/Web/CSS) برای اعمال روی عنصر است. توجه داشته باشید که بهتر است استایل‌ها در یک فایل جداگانه تعریف شوند. این attribute و عنصر [`<style>`](/en-US/docs/Web/HTML/Reference/Element/style) عمدتاً برای استایل سریع، مثلاً در هنگام تست، به کار می‌روند.

```html interactive-example
<div style="background: #ffe7e8; border: 2px solid #e66465">
  <p style="margin: 15px; line-height: 1.5; text-align: center">
    Well, I am the slime from your video<br />
    Oozin' along on your livin' room floor.
  </p>
</div>
```

> [!NOTE]
> این attribute نباید برای انتقال اطلاعات معنایی استفاده شود. حتی اگر تمام استایل‌ها حذف شوند، صفحه باید از نظر معنایی درست باشد. معمولاً نباید از آن برای پنهان کردن اطلاعات بی‌ربط استفاده کرد؛ این کار باید با attribute [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) انجام شود.

## See also

- [Global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- [`HTMLElement.style`](/en-US/docs/Web/API/HTMLElement/style)