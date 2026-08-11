---
title: "<big> HTML bigger text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/big"
translated_by: "n8n + AI"
---

**Element `<big>`** در HTML که منسوخ شده است، متن داخل خود را با اندازه‌ی فونت یک سطح بزرگ‌تر از متن اطراف نمایش می‌دهد (برای مثال `medium` به `large` تبدیل می‌شود). این اندازه به حداکثر سایز مجاز فونت در browser محدود می‌شود.

> **هشدار:** این element از مشخصات استاندارد حذف شده و نباید دیگر استفاده شود. برای تنظیم اندازه‌ی فونت از CSS property `font-size` استفاده کنید.

## Attributes

این element هیچ attribute دیگری به‌جز global attributes که به همه‌ی element ها مشترک است ندارد.

## Examples

در اینجا مثال‌هایی برای استفاده از `<big>` می‌بینید و سپس مثالی که با استفاده از CSS مدرن همان نتیجه را به دست می‌دهد.

### استفاده از `<big>`

این مثال از element منسوخ `<big>` برای بزرگ‌کردن بخشی از متن استفاده می‌کند.

#### HTML

```html
<p>
  This is the first sentence.
  <big>This whole sentence is in bigger letters.</big>
</p>
```

### استفاده از CSS `font-size`

این مثال از CSS property `font-size` برای افزایش اندازه‌ی فونت به اندازه‌ی یک سطح استفاده می‌کند.

#### CSS

```css
.bigger {
  font-size: larger;
}
```

#### HTML

```html
<p>
  This is the first sentence.
  <span class="bigger">This whole sentence is in bigger letters.</span>
</p>
```

## DOM interface

این element اینترفیس `HTMLElement` را پیاده‌سازی می‌کند.

## See also

- CSS: `font-size` ، `font`
- HTML: `<small>` ، `<font>` ، `<style>`