---
title: "<sup> HTML superscript element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/sup"
translated_by: "n8n + AI"
---

عنصر HTML `<sup>` برای نمایش متن به صورت **بالانویس** (supscript) استفاده می‌شود. این کار صرفاً به دلایل تایپوگرافی انجام می‌شود. بالانویس‌ها معمولاً با خط پایهٔ بالاتر و فونت کوچک‌تری نمایش داده می‌شوند.

```html interactive-example
<p>
  The <em>Pythagorean theorem</em> is often expressed as the following equation:
</p>

<p>
  <var>a<sup>2</sup></var> + <var>b<sup>2</sup></var> = <var>c<sup>2</sup></var>
</p>
```

```css interactive-example
p {
  font:
    1rem "Fira Sans",
    sans-serif;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) HTML است.

## نکات استفاده

عنصر `<sup>` را فقط برای اهداف تایپوگرافی استفاده کنید؛ یعنی تغییر موقعیت متن به‌خاطر رعایت استانداردهای تایپوگرافی، نه صرفاً برای ظاهر یا زیبایی.

مثلاً اگر می‌خواهید [علامت تجاری](https://en.wikipedia.org/wiki/Wordmark) یک شرکت یا محصول را با خط پایهٔ بالاتر نمایش دهید، باید از CSS (معمولاً {{cssxref("vertical-align")}}) استفاده کنید، نه `<sup>`. مثلاً با `vertical-align: super` یا اگر بخواهید خط پایه را ۵۰٪ بالا ببرید: `vertical-align: 50%`.

موارد مناسب برای استفاده از `<sup>` عبارت‌اند از (اما محدود به این موارد نیست):

- نمایش توان‌ها، مانند "x<sup>3</sup>". برای موارد پیچیده‌تر بهتر است از [MathML](/en-US/docs/Web/MathML) استفاده کنید. در ادامهٔ همین صفحه مثال [توان‌ها](#exponents) را ببینید.
- نمایش حروف بالانویس (superior lettering) که در برخی زبان‌ها برای مخفف‌ها استفاده می‌شود. مثلاً در فرانسوی کلمه "mademoiselle" را به صورت "M<sup>lle</sup>" مخفف می‌کنند. مثال [حروف بالانویس](#superior_lettering) را ببینید.
- نمایش اعداد ترتیبی (ordinal numbers) مانند "4<sup>th</sup>" به جای "fourth". مثال [اعداد ترتیبی](#ordinal_numbers) را ببینید.

## مثال‌ها

### توان‌ها

توان‌ها یا اعداد به‌توان یکی از رایج‌ترین کاربردهای متن بالانویس هستند. مثال:

```html
<p>
  One of the most common equations in all of physics is <var>E</var>=<var>m</var
  ><var>c</var><sup>2</sup>.
</p>
```

### حروف بالانویس

حروف بالانویس از نظر فنی با بالانویس فرق دارند، اما در HTML معمولاً از `<sup>` برای نمایش آن‌ها استفاده می‌شود. یکی از کاربردهای رایج حروف بالانویس، نمایش مخفف‌های خاص در فرانسوی است:

```html
<p>Robert a présenté son rapport à M<sup>lle</sup> Bernard.</p>
```

### اعداد ترتیبی

اعداد ترتیبی مانند "fourth" در انگلیسی یا "quinto" در اسپانیایی را می‌توان با اعداد و متن خاص هر زبان به صورت بالانویس مخفف کرد:

```html
<p>
  The ordinal number "fifth" can be abbreviated in various languages as follows:
</p>
<ul>
  <li>English: 5<sup>th</sup></li>
  <li>French: 5<sup>ème</sup></li>
</ul>
```

## خلاصهٔ فنی

| ویژگی | مقدار |
|-------|-------|
| **محتوای مجاز** | [متن معمولی](/en-US/docs/Web/HTML/Content_categories#phrasing_content) |
| **حذف تگ** | هیچکدام؛ تگ شروع و پایان اجباری است |
| **والد مجاز** | هر عنصری که [متن معمولی](/en-US/docs/Web/HTML/Content_categories#phrasing_content) را بپذیرد |
| **نقش ARIA پیش‌فرض** | [بدون نقش خاص](https://www.w3.org/TR/html-aria/#dfn-no-corresponding-role) |
| **نقش‌های ARIA مجاز** | هر نقشی |
| **رابط DOM** | [`HTMLElement`](/en-US/docs/Web/API/HTMLElement) |

| ویژگی | مقدار |
|-------|-------|
| [Content categories](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content), palpable content |
| محتوای مجاز | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| حذف تگ | هیچکدام، هر دو تگ شروع و پایان اجباری هستند |
| والدین مجاز | هر عنصری که [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد |
| نقش ARIA ضمنی | [`superscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents) |
| نقش‌های ARIA مجاز | هرکدام |
| رابط DOM | `HTMLElement` |

## Specifications

## Browser compatibility

## همچنین ببینید

- عنصر HTML `<sub>` که زیرنویس تولید می‌کند. توجه داشته باشید که نمی‌توانید همزمان از `sub` و `sup` استفاده کنید. برای تولید همزمان بالانویس و زیرنویس در کنار نماد شیمیایی یک عنصر (که عدد اتمی و عدد جرمی را نشان می‌دهد) باید از MathML استفاده کنید.
- [`<msub>`](/en-US/docs/Web/MathML/Reference/Element/msub)، [`<msup>`](/en-US/docs/Web/MathML/Reference/Element/msup) و [`<msubsup>`](/en-US/docs/Web/MathML/Reference/Element/msubsup) — عناصر MathML.
- خاصیت CSS `vertical-align`.