---
title: "<pre> HTML preformatted text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/pre"
translated_by: "n8n + AI"
---

عنصر `<pre>` در HTML نمایانگر متن پیش‌فرمت (preformatted) است که باید دقیقاً همان‌طور که در فایل HTML نوشته شده نمایش داده شود. این متن معمولاً با فونت غیرموزون یا تک‌فاصله (monospaced) نمایش داده می‌شود.

فضای خالی (whitespace) داخل این عنصر دقیقاً همان‌طور که نوشته شده نمایش داده می‌شود، به‌جز یک استثنا: اگر یک یا چند کاراکتر newline در ابتدای محتوا و بلافاصله بعد از تگ باز `<pre>` قرار داشته باشند، اولین newline حذف می‌شود. این تغییر توسط parser HTML انجام می‌شود و در هنگام استفاده از XHTML اعمال نمی‌شود.

محتوای متنی عناصر `<pre>` به عنوان HTML تجزیه می‌شود، بنابراین اگر می‌خواهید محتوای شما به صورت متن ساده باقی بماند، برخی کاراکترهای نحوی مانند `<` باید با استفاده از character references مربوطه escape شوند. برای اطلاعات بیشتر بخش escaping ambiguous characters را ببینید.

عناصر `<pre>` معمولاً شامل عناصر `<code>`، `<samp>` و `<kbd>` هستند که به ترتیب نمایانگر کد کامپیوتر، خروجی کامپیوتر و ورودی کاربر هستند.

به طور پیش‌فرض، `<pre>` یک عنصر block-level است، یعنی مقدار پیش‌فرض خصوصیت display آن `block` است.

## مثال

```html interactive-example
<pre>
             S
             A
            LUT
             M
            O N
            D  E
            DONT
          JE SUIS
          LA  LAN
          G U E  É
         L O Q U E N
        TE      QUESA
       B  O  U  C  H  E
      O        P A R I S
     T I R E   ET   TIRERA
    T O U             JOURS
   AUX                  A  L
 LEM                      ANDS   - Apollinaire
</pre>
```

```css interactive-example
pre {
  font-size: 0.7rem;
  margin: 0;
}
```

## Attributes

این عنصر فقط شامل ویژگی‌های سراسری (global attributes) است.

- `width` {{deprecated_inline}} {{Non-standard_Inline}}
  - شامل تعداد کاراکتر ترجیحی برای یک خط است. اگرچه از نظر فنی هنوز پیاده‌سازی شده، اما این ویژگی هیچ اثر بصری ندارد؛ برای دستیابی به چنین اثری، از ویژگی CSS `width` استفاده کنید.
- `wrap` {{non-standard_inline}} {{Deprecated_Inline}}
  - نشانه‌ای است که نحوه overflow را مشخص می‌کند. در مرورگرهای مدرن این نشانه نادیده گرفته می‌شود و وجود آن اثر بصری ندارد؛ برای دستیابی به چنین اثری، از ویژگی CSS `white-space` استفاده کنید.

## Accessibility

برای هر تصویر یا نموداری که با استفاده از متن پیش‌فرمت ایجاد شده، ارائه یک توضیح جایگزین (alternate description) مهم است. توضیح جایگزین باید محتوای تصویر یا نمودار را به طور واضح و مختصر توصیف کند.

افرادی که با مشکلات بینایی مواجه هستند و با کمک فناوری‌های کمکی مانند screen reader مرور می‌کنند، ممکن است وقتی کاراکترهای متن پیش‌فرمت به صورت دنباله‌ای خوانده می‌شوند، متوجه نشوند که چه چیزی را نشان می‌دهند.

ترکیبی از عناصر `<figure>` و `<figcaption>` به همراه ویژگی‌های ARIA مانند `role` و `aria-label` روی عنصر `pre`، امکان این را فراهم می‌کند که هنر ASCII پیش‌فرمت به عنوان یک تصویر با متن جایگزین اعلام شود و `figcaption` به عنوان عنوان تصویر عمل کند.

### مثال

```html
<figure>
  <pre role="img" aria-label="ASCII COW">
      ___________________________
  &lt; I'm an expert in my field. &gt;
      ---------------------------
          \   ^__^
           \  (oo)\_______
              (__)\       )\/\
                  ||----w |
                  ||     ||
  </pre>
  <figcaption id="cow-caption">
    گاوی که می‌گوید: «من در حوزه‌ام متخصص هستم.» این گاو با استفاده از کاراکترهای
    پیش‌فرمت شده (preformatted text) نمایش داده شده است.
  </figcaption>
</figure>
```

## مثال‌ها

### مثال پایه

#### HTML

```html
<p>Using CSS to change the font color is easy.</p>
<pre><code>
body {
  color: red;
}
</code></pre>
```

#### نتیجه

(نمونه تعاملی حذف شده است)

### فرار از کاراکترهای مبهم

فرض کنید می‌خواهید کد HTML را درون یک عنصر `<pre>` نمایش دهید. دنباله‌های کاراکتری که تگ‌های معتبر HTML را تعریف می‌کنند (با `<` شروع و با `>` ختم می‌شوند) نمایش داده نمی‌شوند. برای نمایش کاراکترهای تگ به‌صورت متن، باید حداقل کاراکتر `<` را با استفاده از مرجع کاراکتری آن (character reference) escape کنید تا دنباله‌ها دیگر تگ معتبری تعریف نکنند.

در واقعیت، parser HTML اکثر کاراکترها را به‌عنوان متن ساده در نظر می‌گیرد مگر در زمینه‌های خاص. مثلاً `< code` مشکلی ندارد، اما `<code` به اشتباه parse می‌شود؛ `&am;` درست است اما `&amp;` خیر. با این حال، بهتر است تمام کاراکترهای مبهم را escape کنید تا از هرگونه سردرگمی جلوگیری شود، به‌ویژه اگر به‌صورت برنامه‌نویسی HTML تولید می‌کنید و محتوای `<pre>` را تزریق می‌کنید. در این حالت، یک قانون سرانگشتی خوب برای escape کردن کاراکترها به این صورت است:

1. ابتدا محتوا را همان‌طور که می‌خواهید در سند HTML ظاهر شود بنویسید.
2. هر آمپرسند (`&`) را با `&amp;` جایگزین کنید. این مرحله را اول انجام دهید تا کاراکترهای `&` جدیدی که در مرحله بعد ایجاد می‌شوند escape نشوند.
3. هر کاراکتر `<` را با `&lt;` جایگزین کنید.

این کار باعث می‌شود محتوا همان‌طور که انتظار دارید نمایش داده شود. جایگزینی سایر کاراکترهای syntax HTML (مانند `>` با `&gt;`، `"` با `&quot;` و `'` با `&apos;`) اختیاری است، اما ضرری ندارد.

#### HTML

```html
<pre><code>
let i = 5;

if (i &lt; 10 &amp;&amp; i &gt; 0)
  return &quot;Single Digit Number&quot;
</code></pre>
```

#### نتیجه

(نمونه تعاملی حذف شده است)

## خلاصهٔ فنی

| ویژگی | توضیحات |
|-------|-----------|
| دسته‌بندی محتوا (Content categories) | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Content_categories#flow_content), palpable content. |
| محتوای مجاز | [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Content_categories#phrasing_content). |
| حذف تگ | مجاز نیست؛ هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که [flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Content_categories#flow_content) را بپذیرد. |
| نقش ARIA ضمنی | `generic` |
| نقش‌های ARIA مجاز | هر نقش |
| رابط DOM | `HTMLPreElement` |

## سازگاری مرورگر

## همچنین ببینید

- CSS: `white-space`، `word-break`
- مرجع کاراکتر (Character reference)
- المان مرتبط (element): `<code>`، `<samp>`، `<kbd>`