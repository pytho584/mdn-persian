---
title: "<strike> HTML strikethrough element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/strike"
translated_by: "n8n + AI"
---

# `<strike>` — عنصر خط‌خورده HTML

عنصر **`<strike>`** [HTML](/en-US/docs/Web/HTML) متنی را به‌صورت خط‌خورده (خط افقی روی متن) نمایش می‌دهد.

> [!WARNING]
> کاربرد این عنصر در HTML 4 و XHTML 1 منسوخ (deprecated) اعلام شد و در [HTML Living Standard](https://html.spec.whatwg.org/multipage/obsolete.html#strike) به‌کلی متروک (obsolete) شده است. اگر از نظر معنایی مناسب است — یعنی محتوای _حذف‌شده_ را نشان می‌دهد — از `<del>` استفاده کنید. در سایر موارد از `<s>` استفاده کنید.

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## مثال

```html
&lt;strike&gt;: <strike>Today's Special: Salmon</strike> SOLD OUT<br />
&lt;s&gt;: <s>Today's Special: Salmon</s> SOLD OUT
```

## خلاصه فنی

| DOM interface |
|---------------|
| `HTMLElement` |

## جستارهای وابسته

- عنصر `<s>`
- اگر داده‌ها _حذف شده‌اند_ از عنصر `<del>` استفاده کنید.
- از ویژگی CSS `text-decoration` می‌توان برای استایل‌دهی متن با خط‌خورده استفاده کرد.