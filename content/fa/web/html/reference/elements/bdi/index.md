---
title: "<bdi> HTML bidirectional isolate element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/bdi"
translated_by: "n8n + AI"
---

عنصر **`<bdi>`** (مخفف Bidirectional Isolation) به مرورگر می‌گوید متنی که داخل آن قرار دارد را از نظر الگوریتم دوطرفه (bidirectional algorithm) جدا از متن اطرافش در نظر بگیرد. این ویژگی زمانی به کار می‌آید که یک وب‌سایت به صورت پویا متنی را درج می‌کند و از جهت (directionality) آن متن اطلاعی ندارد.

```html interactive-example
<h1>World wrestling championships</h1>

<ul>
  <li><bdi class="name">Evil Steven</bdi>: 1st place</li>
  <li><bdi class="name">François fatale</bdi>: 2nd place</li>
  <li><span class="name">سما</span>: 3rd place</li>
  <li><bdi class="name">الرجل القوي إيان</bdi>: 4th place</li>
  <li><span class="name" dir="auto">سما</span>: 5th place</li>
</ul>
```

```css interactive-example
html {
  font-family: sans-serif;
}

bdi {
  /* Add your styles here */
}

.name {
  color: red;
}
```

متن دوطرفه (bidirectional text) متنی است که هم شامل کاراکترهای چپ‌به‌راست (LTR) و هم راست‌به‌چپ (RTL) باشد – مثلاً یک جملهٔ عربی که درون یک رشتهٔ انگلیسی قرار گرفته است. مرورگرها برای مدیریت این وضعیت از [الگوریتم دوطرفهٔ یونیکد (Unicode Bidirectional Algorithm)](https://www.w3.org/International/articles/inline-bidi-markup/uba-basics) استفاده می‌کنند. در این الگوریتم به هر کاراکتر یک جهت‌گیری ضمنی (implicit directionality) داده می‌شود: مثلاً حروف لاتین LTR و حروف عربی RTL در نظر گرفته می‌شوند. بعضی کاراکترهای دیگر (مثل فاصله و برخی علامت‌های نگارشی) خنثی هستند و جهتشان بر اساس کاراکترهای اطراف تعیین می‌شود.

در بیشتر موارد الگوریتم دوطرفه بدون نیاز به نشانه‌گذاری خاصی کار درستی انجام می‌دهد، اما گاهی به کمک نیاز دارد. اینجا جایی است که `bdi>` وارد عمل می‌شود.

از عنصر `bdi>` برای بستن یک تکه متن استفاده می‌کنیم و به الگوریتم دوطرفه می‌گوییم که این متن را جدا از محیط اطرافش در نظر بگیرد. این کار دو نتیجه دارد:

- جهت‌گیری متنی که درون `bdi>` قرار دارد _روی جهت‌گیری متن اطراف تأثیر نمی‌گذارد_.
- جهت‌گیری متن درون `bdi>` _تحت تأثیر جهت‌گیری متن اطراف قرار نمی‌گیرد_.

برای مثال، متنی مثل این را در نظر بگیرید:

```plain
EMBEDDED-TEXT - 1st place
```

اگر `EMBEDDED-TEXT` چپ‌به‌راست باشد، خروجی درست است. اما اگر راست‌به‌چپ باشد، `- 1` (چون شامل کاراکترهای ضعیف و خنثی است) به‌عنوان متن RTL تفسیر می‌شود و نتیجه به هم می‌ریزد:

```plain
1 - EMBEDDED-TEXTst place
```

اگر از قبل جهت `EMBEDDED-TEXT` را بدانید، می‌توانید این مشکل را با قرار دادن آن درون یک `span>` که ویژگی `dir` آن را به جهت مورد نظر تنظیم کرده‌اید، حل کنید. اما اگر جهت را نمی‌دانید – مثلاً متن از دیتابیس خوانده شده یا کاربر آن را وارد کرده – باید از `bdi>` استفاده کنید تا جهت متن درون آن روی اطراف تأثیر نگذارد.

اگرچه می‌توان همان جلوهٔ بصری را با استفاده از CSS rule (rule) {{cssxref("unicode-bidi", "unicode-bidi: isolate")}} روی یک `span>` یا هر عنصر قالب‌بندی‌کنندهٔ متن دیگر ایجاد کرد، اما توسعه‌دهندگان HTML نباید از این روش استفاده کنند چون معنایی (semantic) نیست و مرورگرها مجاز به نادیده گرفتن استایل CSS هستند.

قرار دادن کاراکترها درون `span dir="auto">` همان اثر `bdi>` را دارد، اما معنای آن کمتر واضح است.

مانند همهٔ عناصر HTML دیگر، این عنصر از [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند؛ با این تفاوت که ویژگی [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) رفتاری غیرعادی دارد: مقدار پیش‌فرض آن `auto` است و هرگز از عنصر والد به ارث برده نمی‌شود. یعنی اگر مقدار `rtl` یا `ltr` را برای `dir` تعیین نکنید، user agent جهت مناسب را بر اساس محتوای داخل `<bdi>` مشخص می‌کند.

## مثال‌ها

### بدون bdi و فقط LTR

در این مثال، برندگان یک مسابقه فقط با استفاده از عناصر `<span>` فهرست شده‌اند. وقتی نام‌ها فقط حاوی متن LTR باشند، نتیجه درست به نظر می‌رسد:

```html
<ul>
  <li><span class="name">Henrietta Boffin</span> - 1st place</li>
  <li><span class="name">Jerry Cruncher</span> - 2nd place</li>
</ul>
```

```css hidden
body {
  border: 1px solid #3f87a6;
  max-width: calc(100% - 40px - 6px);
  padding: 20px;
  width: calc(100% - 40px - 6px);
  border-width: 1px 1px 1px 5px;
}
```

### بدون bdi با متن RTL

در این مثال، برندگان یک مسابقه فقط با عناصر `<span>` فهرست شده‌اند، اما یکی از برنده‌ها نامی با متن RTL دارد. در این حالت، عبارت `- 1` که متشکل از کاراکترهای با جهت خنثی یا ضعیف است، جهت متن RTL را می‌گیرد و نتیجه به‌هم‌ریخته می‌شود:

```html
<ul>
  <li><span class="name">اَلأَعْشَى</span> - 1st place</li>
  <li><span class="name">Jerry Cruncher</span> - 2nd place</li>
</ul>
```

```css hidden
body {
  border: 1px solid #3f87a6;
  max-width: calc(100% - 40px - 6px);
  padding: 20px;
  width: calc(100% - 40px - 6px);
  border-width: 1px 1px 1px 5px;
}
```

### استفاده از bdi با متن LTR و RTL

در این مثال، برندگان مسابقه با عناصر `<bdi>` فهرست شده‌اند. این عناصر به مرورگر می‌گویند که نام را جدا از بافت پیرامونش در نظر بگیرد، بنابراین خروجی مثال به‌درستی مرتب می‌شود:

```html
<ul>
  <li><bdi class="name">اَلأَعْشَى</bdi> - 1st place</li>
  <li><bdi class="name">Jerry Cruncher</bdi> - 2nd place</li>
</ul>
```

```css hidden
body {
  border: 1px solid #3f87a6;
  max-width: calc(100% - 40px - 6px);
  padding: 20px;
  width: calc(100% - 40px - 6px);
  border-width: 1px 1px 1px 5px;
}
```

## خلاصه فنی

## مشخصات عنصر `<bdi>`

| ویژگی | توضیح |
|---|---|
| **دسته‌بندی محتوا** | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، palpable content |
| **محتوا مجاز** | [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| **حذف برچسب** | مجاز نیست. هر دو برچسب شروع و پایان اجباری هستند. |
| **والد مجاز** | هر عنصری که [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| **نقش ARIA ضمنی** | [`generic`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) |
| **نقش‌های ARIA مجاز** | هر نقشی |
| **DOM interface** | [`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement) |

## مشخصات فنی

- [HTML Living Standard – The bdi element](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-bdi-element)
- [HTML 5.2 – The bdi element](https://www.w3.org/TR/html52/textlevel-semantics.html#the-bdi-element)

## سازگاری با مرورگرها

اطلاعات سازگاری در جدول زیر نمایش داده شده است. (جایگزین ماکرو)

## همچنین ببینید

- [Inline markup and bidirectional text in HTML](https://www.w3.org/International/articles/inline-bidi-markup/) – مقاله W3C درباره نشانه‌گذاری درون‌خطی و متن دوجهته
- [Unicode Bidirectional Algorithm basics](https://www.w3.org/International/articles/inline-bidi-markup/uba-basics) – اصول الگوریتم دوجهته یونیکد
- {{Glossary("Localization")}} (محلی‌سازی)
- عنصر HTML مرتبط: {{HTMLElement("bdo")}}
- ویژگی‌های CSS مرتبط: {{cssxref("direction")}} و {{cssxref("unicode-bidi")}}