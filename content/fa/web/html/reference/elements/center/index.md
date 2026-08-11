---
title: "<center> HTML centered text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/center"
translated_by: "n8n + AI"
---

عنصر **`<center>`** یک عنصر [HTML](/en-US/docs/Web/HTML) در سطح بلاک ([block-level element](/en-US/docs/Glossary/Block-level_content)) است که محتوای خود (چه بلاک و چه inline) را به‌صورت افقی در وسط عنصر والد قرار می‌دهد. معمولاً عنصر والد همان {{HTMLElement("body")}} است، اما الزامی نیست.

این تگ در HTML 4 (و XHTML 1) منسوخ (deprecated) اعلام شد و به جای آن باید از خصوصیت [CSS](/en-US/docs/Web/CSS)  {{Cssxref("text-align")}} روی عنصر {{HTMLElement("div")}} یا یک {{HTMLElement("p")}} خاص استفاده کرد. برای وسط‌چین کردن بلاک‌ها، از خصوصیت‌های CSS دیگری مثل {{Cssxref("margin-left")}} و {{Cssxref("margin-right")}} با مقدار `auto` (یا {{Cssxref("margin")}} با مقدار `0 auto`) استفاده کنید.

## DOM interface

این عنصر از {{domxref("HTMLElement")}} پیاده‌سازی می‌کند.

## مثال ۱

```html
<center>
  This text will be centered.
  <p>So will this paragraph.</p>
</center>
```

### نتیجه

{{EmbedLiveSample("Example 1")}}

## مثال ۲ (جایگزین CSS)

```html
<div class="center">
  This text will be centered.
  <p>So will this paragraph.</p>
</div>
```

```css
.center {
  text-align: center;
}
```

### نتیجه

{{EmbedLiveSample("Example 2 (CSS alternative)")}}

## مثال ۳ (جایگزین CSS)

```html
<p class="center">
  This line will be centered.<br />
  And so will this line.
</p>
```

```css
.center {
  text-align: center;
}
```

### نتیجه

{{EmbedLiveSample("Example 3 (CSS alternative)")}}

> [!NOTE]
> اعمال {{cssxref("text-align", "text-align: center")}} روی یک عنصر {{HTMLElement("div")}} یا {{HTMLElement("p")}} باعث می‌شود _محتوای_ آن عنصر وسط‌چین شود، اما ابعاد کلی عنصر تغییری نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- {{Cssxref("text-align")}}
- {{Cssxref("display")}}