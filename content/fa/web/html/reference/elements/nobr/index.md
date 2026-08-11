---
title: "<nobr> HTML non-breaking text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/nobr"
translated_by: "n8n + AI"
---

المان `<nobr>` در [HTML](/en-US/docs/Web/HTML) از شکسته‌شدن خودکار متن داخلش به چند خط جلوگیری می‌کند؛ در نتیجه ممکن است کاربر برای دیدن تمام عرض متن مجبور به اسکرول افقی شود.

> [!WARNING]
> اگرچه این المان به‌طور گسترده پشتیبانی می‌شود، اما هرگز HTML استاندارد نبوده است؛ پس نباید از آن استفاده کنید. به‌جایش از ویژگی CSS `white-space` به این شکل استفاده کنید:

```html
<span class="nobr">Long line with no breaks</span>
```

```css
.nobr {
  white-space: nowrap;
}
```

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- [`white-space`](/en-US/docs/Web/CSS/white-space)
- [`overflow`](/en-US/docs/Web/CSS/overflow)