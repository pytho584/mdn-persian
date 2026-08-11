---
title: "<u> HTML unarticulated annotation (underline) element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/u"
translated_by: "n8n + AI"
---

المان `<u>` در HTML نمایانگر یک بازه از متن درونخطی است که باید بهگونهای رندر شود که نشان دهد یک حاشیهنویسی غیرمتنی دارد. بهصورت پیشفرض این متن با یک خط زیرین ساده و توپر نمایش داده میشود، اما میتوان با CSS آن را تغییر داد.

> [!WARNING]
> این المان در نسخههای قدیمیتر HTML «المان Underline» نامیده میشد و هنوز هم گاهی به همین شکل نادرست استفاده میشود. برای زیرخط دار کردن متن، بهتر است از استایلی استفاده کنید که ویژگی CSS {{cssxref("text-decoration")}} را روی مقدار `underline` تنظیم میکند.

{{InteractiveExample("HTML Demo: &lt;u&gt;", "tabbed-shorter")}}

<!-- cSpell:ignore speling corect -->

```html interactive-example
<p>
  You could use this element to highlight <u>speling</u> mistakes, so the writer
  can <u>corect</u> them.
</p>
```

```css interactive-example
p {
  margin: 0;
}

u {
  text-decoration: red wavy underline;
}
```

برای جزئیات بیشتر درباره اینکه چه زمانی استفاده از `<u>` مناسب است و چه زمانی مناسب نیست، بخش [یادداشتهای استفاده](#usage_notes) را ببینید.

## Attributes

این المان فقط شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) میشود.

## یادداشتهای استفاده

در کنار سایر المانهای صرفاً استایلی، المان اصلی Underline در HTML (یعنی `<u>`) در HTML 4 منسوخ شده بود؛ اما در HTML 5 دوباره با معنای جدید و معنایی (semantic) بازگردانده شد: برای نشان دادن متنی که نوعی حاشیهنویسی غیرمتنی روی آن اعمال شده است.

> [!NOTE]
> از استفاده از المان `<u>` با استایل پیشفرض آن (متن زیرخطدار) بهگونهای که با لینک اشتباه گرفته شود، خودداری کنید؛ زیرا لینکها نیز بهصورت پیشفرض زیرخط دارند.

### موارد استفاده

کاربردهای معتبر برای المان `<u>` عبارتاند از: نشان دادن اشتباهات املایی، اعمال [نشان نام خاص](https://en.wikipedia.org/wiki/Proper_name_mark) برای نمایش اسامی خاص در متن چینی، و سایر انواع حاشیهنویسی.

_نباید_ از `<u>` برای زیرخط دار کردن متن بهمنظور تزئین، یا برای نمایش عنوان کتابها استفاده کنید.

### المانهای دیگری که میتوانید در نظر بگیرید

در بیشتر موارد، بهتر است بهجای `<u>` از المان دیگری استفاده کنید، مانند:

- {{HTMLElement("em")}} برای نشان دادن تأکید
- {{HTMLElement("b")}} برای جلب توجه به متن
- {{HTMLElement("mark")}} برای علامتگذاری کلمات یا عبارات کلیدی
- {{HTMLElement("strong")}} برای نشان دادن اهمیت زیاد متن
- {{HTMLElement("cite")}} برای علامتگذاری عنوان کتابها یا سایر انتشارات
- {{HTMLElement("i")}} برای نشان دادن اصطلاحات فنی، نویسهگردانیها، افکار، یا نام کشتیها در متون غربی

برای ارائه حاشیهنویسی متنی (در مقابل حاشیهنویسی غیرمتنی که با `<u>` ایجاد میشود)، از المان {{HTMLElement("ruby")}} استفاده کنید.

برای اعمال ظاهر زیرخطدار بدون هیچ معنای خاصی، از مقدار `underline` در ویژگی {{cssxref("text-decoration")}} استفاده کنید.

## مثالها

### نشان دادن اشتباه املایی

این مثال از المان `<u>` و کمی CSS استفاده میکند تا پاراگرافی را نمایش دهد که شامل یک کلمه اشتباه املایی است؛ این اشتباه با استایل زیرخط قرمز موجدار نشان داده میشود که معمولاً برای این منظور به کار میرود.

#### HTML

<!-- cSpell:ignore wrnogly -->

```html
<p>This paragraph includes a <u class="spelling">wrnogly</u> spelled word.</p>
```

در HTML، استفاده از `<u>` با یک کلاس به نام `spelling` را میبینیم که برای نشان دادن غلط املایی کلمه «wrongly» به کار رفته است.

#### CSS

```css
u.spelling {
  text-decoration: red wavy underline;
}
```

این CSS مشخص میکند که وقتی المان `<u>` با کلاس `spelling` استایل میشود، باید زیر متن آن یک خط قرمز موجدار باشد. این یک استایل رایج برای اشتباهات املایی است. یک استایل رایج دیگر را میتوان با `red dashed underline` نمایش داد.

#### نتیجه

نتیجه برای هر کسی که از واژهپردازهای محبوب امروزی استفاده کرده باشد آشناست.

{{EmbedLiveSample("Indicating_a_spelling_error", 650, 80)}}

### اجتناب از `<u>`

در بیشتر مواقع، بهتر است از `<u>` استفاده نکنید. در ادامه چند مثال می‌بینید که در هر مورد چه گزینه‌ای مناسب‌تر است.

#### Non-semantic underlines

برای زیرخط‌دار کردن متن بدون ایجاد معنی معنایی، از عنصر `<span>` با خاصیت `text-decoration` به مقدار `"underline"` استفاده کنید، همانطور که در زیر نشان داده شده است.

##### HTML

```html
<span class="underline">Today's Special</span>
<br />
Chicken Noodle Soup With Carrots
```

##### CSS

```css
.underline {
  text-decoration: underline;
}
```

#### Presenting a book title

عنوان کتاب‌ها باید با عنصر `<cite>` نمایش داده شوند، نه با `<u>` یا حتی `<i>`.

##### Using the cite element

```html
<p>The class read <cite>Moby-Dick</cite> in the first term.</p>
```

##### Styling the cite element

استایل پیش‌فرض عنصر `<cite>` متن را به صورت ایتالیک نمایش می‌دهد. می‌توانید با CSS آن را تغییر دهید:

```html
<p>The class read <cite>Moby-Dick</cite> in the first term.</p>
```

```css
cite {
  font-style: normal;
  text-decoration: underline;
}
```

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row"><a href="/en-US/docs/Web/HTML/Guides/Content_categories">Content categories</a></th>
      <td><a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>, <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>, palpable content.</td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td><a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>.</td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>None, both the starting and ending tag are mandatory.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>Any element that accepts <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>.</td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td><code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role">generic</a></code></td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>Any</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## See also

- معمولاً بهتر است از عناصر `<span>`، `<i>`، `<em>`، `<b>` و `<cite>` به جای آن استفاده کنید.
- برای زیرخط‌دار کردن غیرمعنایی، از خاصیت CSS `text-decoration` استفاده کنید.