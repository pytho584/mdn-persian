---
title: "Using microdata in HTML"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Microdata"
translated_by: "n8n + AI"
---

Microdata بخشی از استاندارد HTML در WHATWG است و برای قرار دادن فراداده (metadata) درون محتوای موجود در صفحات وب به کار می‌رود. موتورهای جستجو و خزنده‌های وب می‌توانند microdata را از یک صفحه وب استخراج و پردازش کنند و از آن برای ارائه تجربه مرور غنی‌تر به کاربران استفاده کنند. دسترسی مستقیم به این داده‌های ساختاریافته برای موتورهای جستجو بسیار مفید است، چون به آن‌ها امکان می‌دهد اطلاعات صفحات وب را بهتر درک کنند و نتایج مرتبط‌تری به کاربران نشان دهند. microdata برای توصیف یک item از یک واژگان کمکی و برای تخصیص مقادیر به ویژگی‌های آن از جفت‌های نام-مقدار استفاده می‌کند. در واقع microdata تلاشی است برای ارائه روشی اعلانی (declarative) جهت برچسب‌گذاری عناصر HTML با برچسب‌های قابل خواندن برای ماشین، در مقایسه با رویکردهای مشابهی مانند RDFa و میکروفرمت‌های کلاسیک.

در سطح بالا، microdata از گروهی از جفت‌های نام-مقدار تشکیل شده است. این گروه‌ها item نامیده می‌شوند و هر جفت نام-مقدار یک property است. item‌ها و property‌ها با عناصر معمولی نمایش داده می‌شوند.

- برای ایجاد یک item از attribute «itemscope» استفاده می‌شود.
- برای افزودن یک property به یک item، attribute «itemprop» روی یکی از زیرمجموعه‌های (descendant) آن item قرار می‌گیرد.

## واژگان

گوگل و دیگر موتورهای جستجوی بزرگ از واژگان [Schema.org](https://schema.org/) برای داده‌های ساختاریافته پشتیبانی می‌کنند. این واژگان مجموعه‌ای استاندارد از نام نوع‌ها (type names) و نام property‌ها را تعریف می‌کند؛ برای مثال، [Schema.org Music Event](https://schema.org/MusicEvent) یک اجرای کنسرت را نشان می‌دهد و propertyهای [`startDate`](https://schema.org/startDate) و [`location`](https://schema.org/location) جزئیات کلیدی کنسرت را مشخص می‌کنند. در این حالت، [Schema.org Music Event](https://schema.org/MusicEvent) به‌عنوان URL مورد استفاده در `itemtype` به کار می‌رود و `startDate` و `location` نیز `itemprop`هایی هستند که [Schema.org Music Event](https://schema.org/MusicEvent) تعریف کرده است.

> [!NOTE]
> اطلاعات بیشتر درباره attributeهای `itemtype` در <https://schema.org/Thing> در دسترس است.

واژگان microdata معناشناسی (semantics) یا معنای یک _`Item`_ را فراهم می‌کنند. توسعه‌دهندگان وب می‌توانند یک واژگان سفارشی طراحی کنند یا از واژگان موجود در وب، مانند واژگان پرکاربرد [schema.org](https://schema.org/) استفاده کنند. مجموعه‌ای از واژگان نشانه‌گذاری رایج توسط Schema.org ارائه شده است.

واژگان پرکاربرد:

- آثار خلاقانه: [CreativeWork](https://schema.org/CreativeWork), [Book](https://schema.org/Book), [Movie](https://schema.org/Movie), [MusicRecording](https://schema.org/MusicRecording), [Recipe](https://schema.org/Recipe), [TVSeries](https://schema.org/TVSeries)
- اشیاء غیرمتنی تعبیه‌شده: [AudioObject](https://schema.org/AudioObject), [ImageObject](https://schema.org/ImageObject), [VideoObject](https://schema.org/VideoObject)
- [`Event`](https://schema.org/Event)
- [انواع سلامت و پزشکی](https://schema.org/docs/meddocs.html): نکاتی درباره انواع سلامت و پزشکی در زیرمجموعه [MedicalEntity](https://schema.org/MedicalEntity)
- [`Organization`](https://schema.org/Organization)
- [`Person`](https://schema.org/Person)
- [`Place`](https://schema.org/Place), [LocalBusiness](https://schema.org/LocalBusiness), [Restaurant](https://schema.org/Restaurant)
- [`Product`](https://schema.org/Product), [Offer](https://schema.org/Offer), [AggregateOffer](https://schema.org/AggregateOffer)
- [`Review`](https://schema.org/Review), [AggregateRating](https://schema.org/AggregateRating)
- [`Action`](https://schema.org/Action)
- [`Thing`](https://schema.org/Thing)
- [`Intangible`](https://schema.org/Intangible)

بهره‌برداران اصلی موتورهای جستجو مانند Google، Microsoft و Yahoo! برای بهبود نتایج جستجو به واژگان [schema.org](https://schema.org/) متکی هستند. برای برخی اهداف، یک واژگان ad hoc کافی است؛ برای برخی دیگر، باید واژگان جدیدی طراحی کرد. در صورت امکان، به نویسندگان توصیه می‌شود از واژگان موجود استفاده مجدد کنند، زیرا این کار استفاده مجدد از محتوا را آسان‌تر می‌کند.

در برخی موارد، موتورهای جستجو که مناطق خاصی را پوشش می‌دهند، ممکن است افزونه‌های محلی برای microdata ارائه کنند. مثلاً **Yandex**، موتور جستجوی اصلی در روسیه، از microformatsهایی مثل `hCard` (اطلاعات تماس شرکت)، `hRecipe` (دستور پخت غذا)، `hReview` (نظرات بازار) و `hProduct` (داده‌های محصول) پشتیبانی می‌کند و قالب مخصوص خود را برای تعریف اصطلاحات و مقالات دایرةالمعارفی دارد. این افزونه برای حل مشکلات ترانویسی (transliteration) بین الفبای سیریلیک و لاتین ایجاد شده بود. به لطف پیاده‌سازی پارامترهای نشانه‌گذاری اضافی در واژگان Schema، نمایه‌سازی اطلاعات در صفحات وب روسی‌زبان به‌طور قابل توجهی موفق‌تر شد.

## ویژگی‌های سراسری (Global attributes)

[`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid) – شناسه منحصربه‌فرد جهانی یک آیتم.

[`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop) – برای افزودن ویژگی (property) به یک آیتم استفاده می‌شود. هر المان HTML می‌تواند یک ویژگی `itemprop` داشته باشد که از یک جفت نام و مقدار تشکیل شده است.

[`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref) – ویژگی‌هایی که از نوادگان (descendants) المان دارای `itemscope` نیستند، می‌توانند با استفاده از **itemref** به آیتم مرتبط شوند. `itemref` فهرستی از `id` المان‌ها (نه `itemid`ها) را مشخص می‌کند که ویژگی‌های اضافی در جای دیگری از سند دارند.

[`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope) – ویژگی `itemscope` (معمولاً) همراه با [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype) کار می‌کند تا مشخص کند HTML موجود در یک بلوک درباره یک آیتم خاص است. `itemscope` خودِ _آیتم_ را ایجاد می‌کند و محدوده (scope) نوع آیتم (itemtype) مرتبط با آن را تعریف می‌کند. ویژگی `itemtype` یک URL معتبر از یک واژگان (vocabulary) است (مانند [schema.org](https://schema.org/)) که آیتم و زمینه ویژگی‌های آن را توصیف می‌کند.

[`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype) – URL واژگانی را مشخص می‌کند که برای تعریف `itemprop`ها (ویژگی‌های آیتم) در ساختار داده استفاده می‌شود. ویژگی [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope) برای تعیین محدوده‌ای از ساختار داده که واژگان تعیین‌شده توسط `itemtype` در آن فعال است، به کار می‌رود.

## مثال

### HTML

```html
<div itemscope itemtype="https://schema.org/SoftwareApplication">
  <span itemprop="name">Angry Birds</span> - REQUIRES
  <span itemprop="operatingSystem">ANDROID</span><br />
  <link
    itemprop="applicationCategory"
    href="https://schema.org/SoftwareApplication" />

  <div
    itemprop="aggregateRating"
    itemscope
    itemtype="https://schema.org/AggregateRating">
    RATING:
    <span itemprop="ratingValue">4.6</span> (
    <span itemprop="ratingCount">8864</span> ratings )
  </div>

  <div itemprop="offers" itemscope itemtype="https://schema.org/Offer">
    Price: $<span itemprop="price">1.00</span>
    <meta itemprop="priceCurrency" content="USD" />
  </div>
</div>
```

### داده‌های ساختاریافته (Structured data)

<table class="standard-table">
  <tbody>
    <tr>
      <td rowspan="4">itemscope</td>
      <td>itemtype</td>
      <td colspan="2">
        SoftwareApplication (https://schema.org/SoftwareApplication)
      </td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>Angry Birds</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>operatingSystem</td>
      <td>ANDROID</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>applicationCategory</td>
      <td>SoftwareApplication (https://schema.org/SoftwareApplication)</td>
    </tr>
    <tr>
      <td rowspan="3">itemscope</td>
      <td>itemprop[itemtype]</td>
      <td colspan="2">aggregateRating [AggregateRating]</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>ratingValue</td>
      <td>4.6</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>ratingCount</td>
      <td>8864</td>
    </tr>
    <tr>
      <td rowspan="3">itemscope</td>
      <td>itemprop[itemtype]</td>
      <td colspan="2">offers [Offer]</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>price</td>
      <td>1.00</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>priceCurrency</td>
      <td>USD</td>
    </tr>
  </tbody>
</table>

### نتیجه

> [!NOTE]
> ابزار مفیدی برای استخراج و تأیید ساختارهای microdata در HTML، [Schema Markup Validator](https://validator.schema.org/) است. این ابزار را روی HTML که در بالا نشان داده شد امتحان کنید.

## همچنین ببینید

- [ویژگی‌های سراسری (Global Attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes)