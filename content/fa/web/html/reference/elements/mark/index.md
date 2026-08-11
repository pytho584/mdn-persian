---
title: "<mark> HTML mark text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/mark"
translated_by: "n8n + AI"
---

# `<mark>`

عنصر **`<mark>`** در HTML برای نمایش متنی به کار می‌رود که به دلیل ارتباط آن در بافتار فعلی، **مشخص** یا **هایلایت** شده است. این مشخص‌سازی معمولاً برای ارجاع یا یادداشت‌برداری استفاده می‌شود.

```html interactive-example
<p>Search results for "salamander":</p>

<hr />

<p>
  Several species of <mark>salamander</mark> inhabit the temperate rainforest of
  the Pacific Northwest.
</p>

<p>
  Most <mark>salamander</mark>s are nocturnal, and hunt for insects, worms, and
  other small creatures.
</p>
```

```css interactive-example
mark {
  /* Add your styles here */
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

موارد رایج استفاده از `<mark>` عبارتند از:

- زمانی که درون یک نقل‌قول (`<q>`) یا نقل‌قول بلوکی (`<blockquote>`) به کار می‌رود، معمولاً متنی را نشان می‌دهد که مورد توجه خاصی است ولی در منبع اصلی مشخص نشده، یا متنی که نیاز به بررسی ویژه دارد، حتی اگر نویسندهٔ اصلی آن را مهم ندانسته باشد. این شبیه استفاده از هایلایتر در کتاب برای علامت‌گذاری بخش‌های مورد علاقه است.
- در غیر این صورت، `<mark>` بخشی از محتوای سند را مشخص می‌کند که احتمالاً برای فعالیت فعلی کاربر مرتبط است. مثلاً می‌توان از آن برای نشان‌دادن کلماتی که با یک عملیات جستجو هم‌خوانی دارند استفاده کرد.
- از `<mark>` برای هایلایت نحوی کد استفاده نکنید؛ به جای آن از عنصر `<span>` با CSS مناسب استفاده کنید.

> **توجه:** `<mark>` را با عنصر `<strong>` اشتباه نگیرید. `<mark>` برای نشان‌دادن محتوایی با درجه‌ای از _ارتباط_ استفاده می‌شود، در حالی که `<strong>` نشان‌دهندهٔ بخش‌هایی از متن با _اهمیت_ است.

## دسترس‌پذیری (Accessibility)

وجود عنصر `mark` در پیکربندی پیش‌فرض اغلب صفحه‌خوان‌ها اعلام نمی‌شود. می‌توان با استفاده از ویژگی CSS {{cssxref("content")}} به همراه شبه‌عنصرهای {{cssxref("::before")}} و {{cssxref("::after")}} آن را قابل اعلام کرد.

```css
mark::before,
mark::after {
  clip-path: inset(100%);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

mark::before {
  content: " [highlight start] ";
}

mark::after {
  content: " [highlight end] ";
}
```

برخی از کاربران صفحه‌خوان عمداً اعلام محتوایی که باعث پرگویی می‌شود را غیرفعال می‌کنند. بنابراین مهم است که از این تکنیک سوءاستفاده نشود و فقط در موقعیت‌هایی به کار رود که اگر کاربر از هایلایت شدن محتوا مطلع نشود، درک مطلب دچار مشکل می‌شود.

- [Tweaking Text Level Styles, Reprised](https://adrianroselli.com/2025/04/tweaking-text-level-styles-reprised.html) — Adrian Roselli (2025)
- [Short note on making your mark (more accessible)](https://vispero.com/resources/short-note-on-making-your-mark-more-accessible/) — Vispero (2017)

## مثال‌ها

### علامت‌گذاری متن مورد علاقه

در این مثال اول، از عنصر `<mark>` برای علامت‌گذاری بخشی از یک نقل‌قول استفاده شده که برای کاربر اهمیت ویژه‌ای دارد.

```html
<blockquote>
  It is a period of civil war. Rebel spaceships, striking from a hidden base,
  have won their first victory against the evil Galactic Empire. During the
  battle, <mark>Rebel spies managed to steal secret plans</mark> to the Empire's
  ultimate weapon, the DEATH STAR, an armored space station with enough power to
  destroy an entire planet.
</blockquote>
```

### شناسایی بخش‌های وابسته به بافتار

این مثال نشان می‌دهد که چگونه از `<mark>` برای مشخص‌کردن نتایج جستجو در یک متن استفاده می‌شود.

# `<mark>`

```html
<p>
  It is a dark time for the Rebellion. Although the Death Star has been
  destroyed, <mark class="match">Imperial</mark> troops have driven the Rebel
  forces from their hidden base and pursued them across the galaxy.
</p>

<p>
  Evading the dreaded <mark class="match">Imperial</mark> Starfleet, a group of
  freedom fighters led by Luke Skywalker has established a new secret base on
  the remote ice world of Hoth.
</p>
```

برای تمایز استفاده از `<mark>` در نتایج جستجو از سایر کاربردهای احتمالی، این مثال کلاس سفارشی `"match"` را به هر تطابق اعمال کرده است.

#### Result

## خلاصه فنی

| ویژگی | مقدار |
|-------|-------|
| [انواع محتوا (Content categories)](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content), palpable content. |
| محتوای مجاز (Permitted content) | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| حذف تگ (Tag omission) | هیچکدام، هر دو تگ شروع و پایان الزامی هستند. |
| والدین مجاز (Permitted parents) | هر عنصری که [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را می‌پذیرد. |
| نقش ARIA ضمنی (Implicit ARIA role) | [No corresponding role](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | هرکدام (Any) |
| رابط DOM (DOM interface) | HTMLElement |

## مشخصات فنی

## سازگاری مرورگرها