---
title: "Define terms with HTML"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/How_to/Define_terms_with_HTML"
translated_by: "n8n + AI"
---

## تعریف اصطلاحات با HTML

HTML روش‌های متعددی برای انتقال معنای توصیف فراهم می‌کند؛ چه به‌صورت درون‌خطی (inline) و چه به‌صورت واژه‌نامه‌های ساختاریافته. در این مقاله، نحوهٔ نشانه‌گذاری صحیح کلمات کلیدی هنگام تعریف‌کردن آن‌ها را پوشش می‌دهیم.

<table class="standard-table">
  <tbody>
    <tr>
      <th scope="row">پیش‌نیازها:</th>
      <td>
        باید با نحوهٔ
        <a href="/en-US/docs/Learn_web_development/Getting_started/Your_first_website"
          >create a basic HTML document</a
        >
        آشنا باشید.
      </td>
    </tr>
    <tr>
      <th scope="row">هدف:</th>
      <td>
        یادگیری نحوهٔ معرفی کلمات کلیدی جدید و ساخت فهرست‌های توصیفی (description list).
      </td>
    </tr>
  </tbody>
</table>

وقتی به تعریف یک اصطلاح نیاز دارید، احتمالاً مستقیم به سراغ فرهنگ لغت یا واژه‌نامه می‌روید. فرهنگ‌ها و واژه‌نامه‌ها به‌طور رسمی کلمات کلیدی را با یک یا چند توصیف مرتبط می‌کنند، مانند این مورد:

> - Blue (_Adjective_)
>   - : رنگی مانند آسمان در یک روز آفتابی.
>     _"آسمان آبیِ روشن"_

اما ما پیوسته اصطلاحات را به‌صورت غیررسمی تعریف می‌کنیم، مانند اینجا:

> **Firefox** مرورگری است که توسط بنیاد موزیلا ساخته شده.

برای این موارد، HTML تگ‌هایی برای نشانه‌گذاری توصیف‌ها و واژه‌های توصیف‌شده فراهم می‌کند تا پیام شما به‌درستی به خوانندگان منتقل شود.

## چگونه یک توصیف غیررسمی را نشانه‌گذاری کنیم؟

در کتاب‌های درسی، وقتی یک کلمهٔ کلیدی برای اولین بار ظاهر می‌شود، معمولاً آن را بولد کرده و بلافاصله تعریف می‌کنند. ما در HTML هم همین کار را می‌کنیم، با این تفاوت که HTML یک رسانهٔ بصری نیست و بنابراین از بولد استفاده نمی‌کنیم. به جایش از `<dfn>` استفاده می‌کنیم؛ عنصری ویژه برای نشانه‌گذاری اولین رخداد کلمات کلیدی. توجه کنید که تگ‌های `<dfn>` دورِ _کلمه‌ای که باید تعریف شود_ قرار می‌گیرند، نه دورِ تعریف (تعریف شامل کل پاراگراف است):

```html
<p><dfn>Firefox</dfn> is the web browser created by the Mozilla Foundation.</p>
```

> [!NOTE]
> یکی دیگر از کاربردهای بولد، تأکید بر محتواست. بولد خود مفهومی بیگانه با HTML است، اما [تگ‌هایی برای نشان‌دادن تأکید وجود دارد.](/en-US/docs/Learn_web_development/Core/Structuring_content/Emphasis_and_importance)

### مورد خاص: مخفف‌ها

بهتر است مخفف‌ها را به‌طور ویژه با `<abbr>` نشانه‌گذاری کنید تا صفحه‌خوان‌ها آن‌ها را درست بخوانند و بتوانید روی همهٔ مخفف‌ها به‌صورت یکنواخت عمل کنید. همانند هر کلمهٔ کلیدی جدید، باید مخفف‌ها را در اولین بار وقوع تعریف کنید.

```html
<p>
  <dfn><abbr>HTML</abbr> (hypertext markup language)</dfn>
  is a description language used to structure documents on the web.
</p>
```

> [!NOTE]
> مشخصات HTML در واقع ویژگی `title` را برای گسترش مخفف در نظر گرفته است. با این حال، این جایگزین مناسبی برای ارائهٔ یک بسط درون‌خطی نیست. محتوای `title` کاملاً از کاربران شما پنهان است، مگر اینکه با ماوس روی مخفف هاور کنند. مشخصات به‌درستی [این موضوع را نیز اذعان می‌کند.](https://html.spec.whatwg.org/multipage/dom.html#attr-title)

### بهبود دسترس‌پذیری

`<dfn>` کلمهٔ کلیدی تعریف‌شده را نشانه‌گذاری می‌کند و نشان می‌دهد که پاراگراف فعلی آن کلمه را تعریف می‌کند. به عبارت دیگر، یک رابطهٔ ضمنی بین عنصر `<dfn>` و ظرفِ آن وجود دارد. اگر رابطهٔ رسمی‌تری می‌خواهید، یا تعریف شما فقط یک جمله است نه کل پاراگراف، می‌توانید از ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) برای ارتباط رسمی‌تر یک اصطلاح با تعریفش استفاده کنید:

```markdown
```html
<p>
  <span id="ff">
    <dfn aria-describedby="ff">Firefox</dfn>
    is the web browser created by the Mozilla Foundation.
  </span>
  You can download it at <a href="https://www.mozilla.org">mozilla.org</a>
</p>
```

فناوری کمکی (Assistive Technology) اغلب می‌تواند از این attribute برای یافتن متن جایگزین برای یک عبارت استفاده کند. می‌توانید `aria-describedby` را روی هر تگی که یک کلمه‌ی کلیدی را در بر می‌گیرد استفاده کنید (نه فقط element مربوط به `<dfn>`). `aria-describedby` به [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) element‌ای که توضیح را در بر دارد اشاره می‌کند.

## چگونه یک لیست توضیحات بسازیم

لیست‌های توضیحات دقیقاً همان چیزی هستند که ادعا می‌کنند: فهرستی از اصطلاحات و توضیحات مربوط به آن‌ها (مثلاً لیست‌های تعریف، مدخل‌های دیکشنری، سوالات متداول، و جفت‌های کلید-مقدار).

> [!NOTE]
> لیست‌های توضیحات برای نشانه‌گذاری گفتگو [مناسب نیستند](https://html.spec.whatwg.org/multipage/grouping-content.html#the-dl-element)، زیرا مکالمه مستقیماً سخنگویان را توصیف نمی‌کند. در اینجا [توصیه‌هایی برای نشانه‌گذاری گفتگو](https://html.spec.whatwg.org/multipage/semantics-other.html#conversations) ارائه شده است.

اصطلاحاتی که توضیح داده می‌شوند داخل elementهای `<dt>` قرار می‌گیرند. توضیح مربوطه بلافاصله بعد از آن، در یک یا چند element ی `<dd>` می‌آید. کل لیست توضیحات را با یک element ی `<dl>` محصور کنید.

### یک مثال ساده

در اینجا مثالی برای توصیف انواع غذا و نوشیدنی آمده است:

```html
<dl>
  <dt>jambalaya</dt>
  <dd>
    rice-based entree typically containing chicken, sausage, seafood, and spices
  </dd>

  <dt>sukiyaki</dt>
  <dd>
    Japanese specialty consisting of thinly sliced meat, vegetables, and
    noodles, cooked in sake and soy sauce
  </dd>

  <dt>chianti</dt>
  <dd>dry Italian red wine originating in Tuscany</dd>
</dl>
```

> [!NOTE]
> همان‌طور که می‌بینید، الگوی پایه این است که بین `<dt>` و `<dd>` تناوب برقرار شود. اگر دو یا چند اصطلاح پشت سر هم بیایند، توضیح بعدی به همه‌ی آن‌ها اعمال می‌شود. اگر دو یا چند توضیح پشت سر هم بیایند، همه به آخرین اصطلاح داده‌شده مربوط می‌شوند.

### بهبود خروجی بصری

اگر می‌خواهید کلیدواژه‌ها بیشتر برجسته شوند، می‌توانید آن‌ها را ضخیم کنید. به یاد داشته باشید که HTML یک رسانه بصری نیست؛ برای همه‌ی جلوه‌های بصری به CSS نیاز داریم. در اینجا به property ی CSS با نام `font-weight` نیاز دارید:

```css
dt {
  font-weight: bold;
}
```

این کار باعث می‌شود نتیجه کمی خواناتر شود.

## بیشتر بدانید

- `<dfn>`
- `<dl>`
- `<dt>`
- `<dd>`
- [نحوه استفاده از attribute ی aria-describedby](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
```