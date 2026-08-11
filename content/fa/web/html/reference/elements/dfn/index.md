---
title: "<dfn> HTML definition element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dfn"
translated_by: "n8n + AI"
---

عنصر `<dfn>` در HTML — عنصر تعریف (Definition Element)

عنصر **`<dfn>`** در HTML نشان‌دهندهٔ یک اصطلاح است که قرار است تعریف شود. از `<dfn>` باید در یک جملهٔ کامل تعریف استفاده کرد، جایی که تعریف کامل آن اصطلاح می‌تواند یکی از موارد زیر باشد:

- پاراگراف بالادستی (یک بلوک متن، که معمولاً با عنصر {{HTMLElement("p")}} مشخص می‌شود)
- جفت‌عنصر {{HTMLElement("dt")}} / {{HTMLElement("dd")}}
- نزدیک‌ترین بخش بالادستی (section ancestor) عنصر `<dfn>`

```html interactive-example
<p>
  A <dfn id="def-validator">validator</dfn> is a program that checks for syntax
  errors in code or documents.
</p>
```

```css interactive-example
dfn {
  /* Add your styles here */
}
```

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) در اینجا معنای خاصی دارد که در ادامه توضیح داده شده است.

## نکات استفاده

برخی جنبه‌های استفاده از `<dfn>` کاملاً آشکار نیستند. در اینجا به آن‌ها می‌پردازیم.

### تعیین اصطلاح مورد نظر

اصطلاحی که تعریف می‌شود طبق قوانین زیر مشخص می‌شود:

1. اگر عنصر `<dfn>` دارای ویژگی `title` باشد، مقدار آن به‌عنوان اصطلاح تعریف‌شده در نظر گرفته می‌شود. عنصر همچنان باید متن درون خود را داشته باشد، اما آن متن می‌تواند یک مخفف (مثلاً با {{HTMLElement("abbr")}}) یا شکل دیگری از اصطلاح باشد.
2. اگر `<dfn>` فقط یک عنصر فرزند داشته باشد و خودش متن مستقیمی نداشته باشد، و آن عنصر فرزند یک {{HTMLElement("abbr")}} با ویژگی `title` باشد، مقدار `title` آن `<abbr>` دقیقاً همان اصطلاح تعریف‌شده است.
3. در غیر این صورت، محتوای متنی خود عنصر `<dfn>` اصطلاح تعریف‌شده است. این مورد در [مثال اول](#basic-identification-of-a-term) نشان داده شده است.

> **نکته:** اگر عنصر `<dfn>` دارای ویژگی `title` باشد، _باید_ فقط حاوی اصطلاح تعریف‌شده باشد و هیچ متن دیگری نداشته باشد.

### پیوند به عناصر `<dfn>`

اگر یک ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) به `<dfn>` اضافه کنید، می‌توانید با عناصر {{HTMLElement("a")}} به آن پیوند دهید. این پیوندها باید به‌عنوان استفاده از اصطلاح باشند، به‌طوری که خواننده بتواند با کلیک روی پیوند اصطلاح، سریعاً به تعریف آن برود (اگر از قبل آن را نمی‌داند).

این مورد در مثال [پیوند به تعریف‌ها](#links-to-definitions) در پایین نشان داده شده است.

## مثال‌ها

بیایید چند نمونه از سناریوهای مختلف استفاده را بررسی کنیم.

### شناسایی پایهٔ یک اصطلاح

این مثال از یک `<dfn>` ساده برای مشخص کردن محل یک اصطلاح درون تعریف استفاده می‌کند.

#### HTML

```html
<p>
  The <strong>HTML Definition element (<dfn>&lt;dfn&gt;</dfn>)</strong> is used
  to indicate the term being defined within the context of a definition phrase
  or sentence.
</p>
```

از آن‌جایی که عنصر `<dfn>` ویژگی `title` ندارد، محتوای متنی خود عنصر `<dfn>` به‌عنوان اصطلاح تعریف‌شده استفاده می‌شود.

#### نتیجه

### پیوند به تعریف‌ها

برای افزودن پیوند به تعریف‌ها، کافی است مانند همیشه از عنصر {{HTMLElement("a")}} استفاده کنید.

#### HTML

```html-nolint
<p>
  The
  <strong>HTML Definition element (<dfn id="definition-dfn">&lt;dfn&gt;</dfn>)</strong>
  is used to indicate the term being defined within the context of a definition
  phrase or sentence.
</p>
```

به دلیل تمام این موارد، ما تصمیم گرفتیم از عنصر `<dfn>` برای این پروژه استفاده کنیم.

در اینجا تعریف را می‌بینید — اکنون با یک ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) به نام `"definition-dfn"` که می‌تواند به عنوان هدف یک لینک استفاده شود. بعداً، یک لینک با استفاده از `<a>` با ویژگی [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) برابر با `"#definition-dfn"` ایجاد می‌شود تا به تعریف بازگردد.

#### Result

### استفاده از مخفف‌ها و تعاریف با هم

در برخی موارد، ممکن است بخواهید هنگام تعریف یک اصطلاح، از مخفف آن استفاده کنید. این کار با استفاده از عناصر `<dfn>` و `<abbr>` به صورت ترکیبی انجام می‌شود:

#### HTML

```html
<p>
  The <dfn><abbr title="Hubble Space Telescope">HST</abbr></dfn> is among the
  most productive scientific instruments ever constructed. It has been in orbit
  for over 20 years, scanning the sky and returning data and photographs of
  unprecedented quality and detail.
</p>

<p>
  Indeed, the <abbr title="Hubble Space Telescope">HST</abbr> has arguably done
  more to advance science than any device ever built.
</p>
```

توجه داشته باشید که عنصر `<abbr>` درون `<dfn>` قرار گرفته است. اولی مشخص می‌کند که این اصطلاح یک مخفف است ("HST") و عبارت کامل ("Hubble Space Telescope") را در ویژگی `title` خود ذکر می‌کند. دومی نشان می‌دهد که این عبارت مخفف، اصطلاحی است که در حال تعریف آن هستیم.

#### Result

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">Palpable content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>،
        اما هیچ عنصر `<dfn>` نباید در داخل آن به عنوان فرزند وجود داشته باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچکدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role"><code>term</code></a></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هرنقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- عناصر مرتبط با لیست تعریف: <a href="/en-US/docs/Web/HTML/Element/dl">&lt;dl&gt;</a>، <a href="/en-US/docs/Web/HTML/Element/dt">&lt;dt&gt;</a>، <a href="/en-US/docs/Web/HTML/Element/dd">&lt;dd&gt;</a>
- <a href="/en-US/docs/Web/HTML/Element/abbr">&lt;abbr&gt;</a>