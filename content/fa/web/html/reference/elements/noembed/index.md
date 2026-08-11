---
title: "<noembed> HTML embed fallback element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/noembed"
translated_by: "n8n + AI"
---

عنصر `<noembed>` یک عنصر منسوخ و غیراستاندارد در HTML است که برای ارائه محتوای جایگزین (fallback) به مرورگرهایی استفاده می‌شد که عنصر {{HTMLElement("embed")}} یا نوع خاصی از [محتوای جاسازی‌شده](/en-US/docs/Web/HTML/Guides/Content_categories#embedded_content) را پشتیبانی نمی‌کردند. این عنصر از HTML 4.01 به بعد منسوخ اعلام شد و به جای آن باید محتوای جایگزین را بین تگ باز و بسته عنصر {{HTMLElement("object")}} قرار داد.

> **توجه:**
> اگرچه این عنصر در بسیاری از مرورگرها هنوز کار می‌کند، اما منسوخ شده و نباید استفاده شود. به جای آن از {{HTMLElement("object")}} با محتوای جایگزین بین تگ باز و بسته استفاده کنید.

## مثال‌ها

پیام داخل تگ `<noembed>` فقط زمانی نمایش داده می‌شود که مرورگر شما از تگ `<embed>` پشتیبانی نکند.

### نمایش محتوای جایگزین

```html
<embed
  type="vide/webm"
  src="/media/examples/flower.mp4"
  width="200"
  height="200" />
<noembed>
  <h1>Alternative content</h1>
</noembed>
```