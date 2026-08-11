---
title: "itemtype HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype"
translated_by: "n8n + AI"
---

ویژگی سراسری (global attribute) **`itemtype`** آدرس (URL) واژگان (vocabulary) را مشخص می‌کند که برای تعریف `itemprop`ها (ویژگی‌های آیتم) در ساختار داده استفاده خواهد شد.

[`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope) برای تنظیم محدوده‌ای استفاده می‌شود که در آن، واژگان تعیین‌شده توسط `itemtype` در ساختار داده فعال خواهد بود.

گوگل و دیگر موتورهای جستجوی مهم از واژگان [schema.org](https://schema.org/) برای داده‌های ساختاریافته پشتیبانی می‌کنند. این واژگان مجموعه‌ای استاندارد از نام نوع‌ها (type names) و نام ویژگی‌ها (property names) ارائه می‌دهد. برای مثال، `MusicEvent` به یک اجرای کنسرت اشاره دارد و ویژگی‌های [`startDate`](https://schema.org/startDate) و [`location`](https://schema.org/location) جزئیات کلیدی کنسرت را مشخص می‌کنند. در این حالت، [`MusicEvent`](https://schema.org/MusicEvent) همان آدرسی است که در `itemtype` استفاده می‌شود و `startDate` و `location` به‌عنوان `itemprop`هایی هستند که [`MusicEvent`](https://schema.org/MusicEvent) آن‌ها را تعریف می‌کند.

> [!NOTE]
> اطلاعات بیشتر درباره ویژگی‌های `itemtype` را می‌توانید در <https://schema.org/Thing> بیابید.

- ویژگی **`itemtype`** باید مقداری داشته باشد که مجموعه‌ای نامرتب از توکن‌های یکتا باشد. این توکن‌ها به بزرگی/کوچکی حروف حساسند (case-sensitive)، هرکدام باید یک URL معتبر و مطلق باشند و همگی باید با یک واژگان یکسان تعریف شده باشند. مقدار ویژگی باید حداقل یک توکن داشته باشد.
- نوع‌های آیتم (item types) باید همگی نوع‌هایی باشند که در مشخصات قابل‌اعمال (مانند [schema.org](https://schema.org/)) تعریف شده‌اند و همگی برای استفاده با همان واژگان تعریف شده باشند.
- ویژگی `itemtype` فقط روی عنصرهایی قابل تنظیم است که ویژگی `itemscope` روی آن‌ها مشخص شده باشد.
- ویژگی `itemid` فقط روی عنصرهایی قابل تنظیم است که هم ویژگی `itemscope` و هم ویژگی `itemtype` روی آن‌ها مشخص شده باشد. این ویژگی فقط باید روی عنصرهایی تنظیم شود که دارای ویژگی `itemscope` هستند و ویژگی `itemtype` آن‌ها واژگانی را تعیین می‌کند که طبق تعریف آن واژگان، از شناسه‌های سراسری (global identifiers) برای آیتم‌ها پشتیبانی نمی‌کند.
- معنای دقیق یک شناسه سراسری توسط مشخصات همان واژگان تعیین می‌شود. تعیین اینکه آیا چند آیتم با شناسه سراسری یکسان (خواه در یک صفحه یا صفحات مختلف) مجاز هستند و همچنین قوانین پردازش مربوط به آن واژگان در صورت وجود چند آیتم با شناسه یکسان، به مشخصات همان واژگان واگذار شده است.

## مثال‌ها

### نمایش داده‌های ساختاریافته برای یک محصول

این مثال از ویژگی‌های microdata برای نمایش داده‌های ساختاریافته یک محصول استفاده می‌کند، به این صورت:

<table class="standard-table">
  <tbody>
    <tr>
      <td rowspan="7">itemscope</td>
      <td>itemtype</td>
      <td colspan="2">Product (https://schema.org/Product)</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>Executive Anvil</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>image</td>
      <td>
        https://pixabay.com/static/uploads/photo/2015/09/05/18/15/suitcase-924605_960_720.png
      </td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>description</td>
      <td>
        Executive Anvil نسبت به سندان کلاسیک ACME باریک‌تر است و برای مسافر
        تجاری‌ای که به دنبال چیزی برای انداختن از ارتفاع است، عالی است.
      </td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>mpn</td>
      <td>925872</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>brand [Thing]</td>
      <td></td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>ACME</td>
    </tr>
    <tr>
      <td rowspan="9">itemscope</td>
      <td>itemprop[itemtype]</td>
      <td>aggregateRating[AggregateRating]</td>
      <td></td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>ratingValue</td>
      <td>4.4</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>reviewCount</td>
      <td>89</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>offers [Offer]</td>
      <td>https://schema.org/Offer</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>priceCurrency</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>price</td>
      <td>119.99</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>priceValidUntil</td>
      <td>2020-11-05</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>itemCondition</td>
      <td>https://schema.org/UsedCondition</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>availability</td>
      <td>https://schema.org/InStock</td>
    </tr>
    <tr>
      <td rowspan="2">itemscope</td>
      <td>itemprop[itemtype]</td>
      <td>seller [Organization]</td>
      <td>https://schema.org/Organization</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>Executive Objects</td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> ابزار [Structured Data Testing Tool](https://developers.google.com/search/docs/appearance/structured-data) گوگل، ابزار کاربردی‌ای برای استخراج ساختارهای microdata از HTML است. می‌توانید آن را روی HTML نشان‌داده‌شده در همین‌جا امتحان کنید.

#### HTML

```html
<div itemscope itemtype="https://schema.org/Product">
  <span itemprop="brand">ACME<br /></span>
  <span itemprop="name">Executive Anvil<br /></span>
  <img
    itemprop="image"
    src="https://pixabay.com/static/uploads/photo/2015/09/05/18/15/suitcase-924605_960_720.png"
    width="50"
    height="50"
    alt="Executive Anvil logo" /><br />

  <span itemprop="description">
    Sleeker than ACME's Classic Anvil, the Executive Anvil is perfect for the
    business traveler looking for something to drop from a height.
    <br />
  </span>
```

Product #: <span itemprop="mpn">925872<br /></span>
  <span
    itemprop="aggregateRating"
    itemscope
    itemtype="https://schema.org/AggregateRating">
    Rating: <span itemprop="ratingValue">4.4</span> stars, based on
    <span itemprop="reviewCount">89 </span> reviews
  </span>
  <p>
    <span itemprop="offers" itemscope itemtype="https://schema.org/Offer">
      Regular price: $179.99<br />
      <meta itemprop="priceCurrency" content="USD" />
      <span itemprop="price">Sale price: $119.99<br /></span>
      (Sale ends
      <time itemprop="priceValidUntil" datetime="2020-11-05">5 November!</time>)
      <br />
      Available from:
      <span
        itemprop="seller"
        itemscope
        itemtype="https://schema.org/Organization">
        <span itemprop="name">Executive Objects<br /></span>
      </span>
      Condition:
      <link
        itemprop="itemCondition"
        href="https://schema.org/UsedCondition" />Previously owned, in excellent
      condition<br />
      <link itemprop="availability" href="https://schema.org/InStock" />In
      stock! Order now!
    </span>
  </p>
</div>

#### نتیجه

## مشخصات

## همچنین ببینید

- [Other different global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- سایر global attributes مرتبط با microdata:
  - [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - [`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref)
  - [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)