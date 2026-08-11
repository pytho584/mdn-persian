---
title: "<abbr> HTML abbreviation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/abbr"
translated_by: "n8n + AI"
---

The **`<abbr>`** [HTML](/en-US/docs/Web/HTML) element نشان‌دهندهٔ یک کوتاه‌نویسی (abbreviation) یا سرواژه (acronym) است.

هنگامی که از یک کوتاه‌نویسی یا سرواژه استفاده می‌کنید، در اولین بار، توضیح کامل آن را به صورت متن ساده (plain text) در کنار `<abbr>` قرار دهید تا معنی آن برای کاربر مشخص شود.

ویژگی اختیاری [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) می‌تواند توضیح کوتاه‌نویسی را در مواقعی که توضیح کامل در متن نیست ارائه دهد. این ویژگی به عامل کاربر (user agent) کمک می‌کند نحوه‌ی اعلام/نمایش محتوا را تعیین کند و هم‌زمان به همه‌ی کاربران نشان دهد که کوتاه‌نویسی به چه معناست. اگر وجود داشته باشد، `title` باید فقط همین توضیح کامل را داشته باشد و نه چیز دیگر.

```html
<p>
  You can use <abbr>CSS</abbr> (Cascading Style Sheets) to style your
  <abbr>HTML</abbr> (HyperText Markup Language). Using style sheets, you can
  keep your <abbr>CSS</abbr> presentation layer and <abbr>HTML</abbr> content
  layer separate. This is called "separation of concerns."
</p>
```

```css
abbr {
  font-style: italic;
  color: chocolate;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط از [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند. ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) هنگامی که با `<abbr>` استفاده می‌شود یک معنای خاص دارد: باید یک توضیح یا بسط قابل‌خواندن توسط انسان از کوتاه‌نویسی را داشته باشد. این متن معمولاً توسط مرورگرها به صورت tooltip هنگام قرار گرفتن ماوس روی عنصر نمایش داده می‌شود.

هر `<abbr>` که استفاده می‌کنید مستقل از بقیه است؛ تعیین `title` برای یکی به طور خودکار همان توضیح را برای دیگر عناصر با محتوای یکسان اعمال نمی‌کند.

## نکات استفاده

### موارد کاربرد معمول

قطعاً لازم نیست همهٔ کوتاه‌نویسی‌ها با `<abbr>` مشخص شوند. با این حال، چند مورد وجود دارد که این کار مفید است:

- اگر از یک کوتاه‌نویسی استفاده می‌کنید و می‌خواهید توضیح یا تعریفی خارج از جریان محتوای مستند ارائه دهید، از `<abbr>` با [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) مناسب استفاده کنید.
- برای تعریف کوتاه‌نویسی‌ای که ممکن است برای خواننده ناآشنا باشد، عبارت را با `<abbr>` و متن توضیح‌دهنده درون خط (inline) ارائه دهید. فقط در صورتی از ویژگی `title` استفاده کنید که توضیح یا تعریف درون خط موجود نباشد.
- وقتی نیاز است وجود یک کوتاه‌نویسی در متن از نظر معنایی نشان داده شود، عنصر `<abbr>` مفید است. این کار می‌تواند برای اهداف استایل‌دهی یا اسکریپت‌نویسی استفاده شود.
- می‌توانید از `<abbr>` به همراه {{HTMLElement("dfn")}} برای تعریف اصطلاحاتی که کوتاه‌نویسی یا سرواژه هستند استفاده کنید. به مثال [تعریف یک کوتاه‌نویسی](#تعریف-یک-کوتاه‌نویسی) در پایین مراجعه کنید.

### ملاحظات دستوری (Grammar considerations)

در زبان‌هایی که [عدد دستوری (grammatical number)](https://en.wikipedia.org/wiki/Grammatical_number) دارند (یعنی زبان‌هایی که تعداد اشیاء بر دستور جمله تأثیر می‌گذارد)، از همان عدد دستوری در ویژگی `title` استفاده کنید که در داخل `<abbr>` دارید. این موضوع مخصوصاً در زبان‌هایی با بیش از دو عدد (مانند عربی) مهم است، اما در انگلیسی هم کاربرد دارد.

## استایل پیش‌فرض (Default styling)

هدف این عنصر صرفاً برای راحتی نویسنده است و همهٔ مرورگرها آن را به صورت inline نمایش می‌دهند ({{cssxref("display", "display: inline")}})، اگرچه استایل پیش‌فرض آن از مرورگری به مرورگر دیگر متفاوت است.

برخی مرورگرها زیر محتوای عنصر یک خط‌چین اضافه می‌کنند. برخی دیگر ضمن تبدیل محتوا به حروف کوچک (small caps) این کار را انجام می‌دهند. بعضی مرورگرها هم ممکن است آن را مشابه یک عنصر `<span>` استایل ندهند. برای کنترل این استایل‌بندی از `text-decoration` و `font-variant` استفاده کنید.

## Accessibility

نوشتن کامل مخفف یا اختصار در اولین باری که در یک صفحه به کار می‌رود، به فهم آن کمک می‌کند — به‌ویژه اگر محتوا فنی یا شامل اصطلاحات تخصصی باشد.

فقط در صورتی از ویژگی `title` استفاده کنید که امکان بسط مخفف درون متن وجود نداشته باشد. اگر بین کلمه یا عبارتی که اعلام می‌شود و چیزی که روی صفحه نمایش داده می‌شود تفاوت وجود داشته باشد (به‌خصوص اگر اصطلاح فنی باشد که خواننده ممکن است نداند)، می‌تواند گیج‌کننده باشد.

```html
<p>
  JavaScript Object Notation (<abbr>JSON</abbr>) is a lightweight
  data-interchange format.
</p>
```

این مطلب به‌ویژه برای کسانی مفید است که با اصطلاحات یا مفاهیم مطرح‌شده در محتوا آشنا نیستند، افرادی که تازه زبان را یاد می‌گیرند و کسانی که مشکلات شناختی دارند.

## Examples

### نشانه‌گذاری معنایی یک مخفف

برای نشانه‌گذاری یک مخفف بدون ارائهٔ بسط یا توضیح، از `<abbr>` بدون هیچ ویژگی استفاده کنید، همان‌طور که در این مثال دیده می‌شود.

#### HTML

```html
<p>Using <abbr>HTML</abbr> is fun and easy!</p>
```

#### Result

### استایل‌دهی به مخفف‌ها

می‌توانید با CSS یک استایل سفارشی برای مخفف‌ها تنظیم کنید، مانند این مثال پایه.

#### HTML

```html
<p>Using <abbr>CSS</abbr>, you can style your abbreviations!</p>
```

#### CSS

```css
abbr {
  font-variant: all-small-caps;
}
```

#### Result

### ارائهٔ بسط مخفف

اضافه کردن ویژگی `title` به شما امکان می‌دهد بسط یا تعریفی برای مخفف یا اختصار ارائه دهید.

#### HTML

```html
<p>Ashok's joke made me <abbr title="Laugh Out Loud">LOL</abbr> big time.</p>
```

#### Result

### تعریف یک مخفف

می‌توانید از `<abbr>` همراه با `<dfn>` استفاده کنید تا یک مخفف را به صورت رسمی‌تر تعریف کنید، همان‌طور که در زیر نشان داده شده است.

#### HTML

```html
<p>
  <dfn id="html"><abbr title="HyperText Markup Language">HTML</abbr> </dfn> is a
  markup language used to create the semantics and structure of a web page.
</p>

<p>
  A <dfn id="spec">Specification</dfn> (<abbr>spec</abbr>) is a document that
  outlines in detail how a technology or API is intended to function and how it
  is accessed.
</p>
```

#### Result

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا (Content categories)</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>،
        palpable content
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف برچسب (Tag omission)</th>
      <td>هیچکدام – هر دو برچسب شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">هیچ نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM Interface)</th>
      <td>HTMLElement</td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility

## See also

- [استفاده از عنصر `<abbr>`](/en-US/docs/Learn_web_development/Core/Structuring_content/Advanced_text_features#abbreviations)