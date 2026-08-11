---
title: "itemtype HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype"
translated_by: "n8n + AI"
---

attribute سراسری **`itemtype`** URL واژگان (vocabulary) را مشخص می‌کند که برای تعریف `itemprop`ها (property های آیتم) در ساختار داده استفاده می‌شود.

از [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope) برای تعیین محدوده‌ای در ساختار داده استفاده می‌شود که واژگان تعیین‌شده توسط `itemtype` در آن فعال خواهد بود.

گوگل و دیگر موتورهای جستجوی اصلی از واژگان [schema.org](https://schema.org/) برای داده‌های ساختاریافته پشتیبانی می‌کنند. این واژگان مجموعه‌ای استاندارد از نام typeها و propertyها را تعریف می‌کند. برای مثال، `MusicEvent` یک اجرای کنسرت را نشان می‌دهد و property های [`startDate`](https://schema.org/startDate) و [`location`](https://schema.org/location) جزئیات کلیدی کنسرت را مشخص می‌کنند. در این حالت، [`MusicEvent`](https://schema.org/MusicEvent) همان URL مورد استفاده برای `itemtype` است و `startDate` و location به‌عنوان `itemprop`هایی هستند که [`MusicEvent`](https://schema.org/MusicEvent) تعریف می‌کند.

> [!NOTE]
> اطلاعات بیشتر درباره attributeهای `itemtype` در آدرس <https://schema.org/Thing> موجود است.

- attribute **`itemtype`** باید مقداری داشته باشد که مجموعه‌ای بدون ترتیب از token های یکتا و case-sensitive باشد؛ هر token یک URL معتبر و مطلق است و همگی باید از یک واژگان استفاده کنند. مقدار این attribute باید حداقل یک token داشته باشد.
- type های آیتم باید همگی type هایی باشند که در مشخصات مربوطه (مانند [schema.org](https://schema.org/)) تعریف شده‌اند و همگی برای استفاده از یک واژگان تعریف شده باشند.
- attribute `itemtype` فقط روی elementهایی قابل استفاده است که attribute `itemscope` داشته باشند.
- attribute `itemid` فقط روی elementهایی قابل استفاده است که هم attribute `itemscope` و هم attribute `itemtype` داشته باشند. این attribute فقط باید روی elementهایی با `itemscope` مشخص شود که attribute `itemtype` آن‌ها واژگانی را تعیین می‌کند که طبق مشخصات آن واژگان، از شناسه‌های سراسری (global identifier) برای آیتم‌ها پشتیبانی نمی‌کند.
- معنای دقیق یک شناسه سراسری توسط مشخصات واژگان تعیین می‌شود. این مشخصات تعیین می‌کنند که آیا چند آیتم با شناسه سراسری یکسان (خواه در یک صفحه یا صفحات مختلف) مجاز هستند و همچنین قوانین پردازش آن واژگان در مواجهه با چند آیتم با شناسه یکسان چگونه است.

## مثال‌ها

### نمایش داده‌های ساختاریافته برای یک محصول

این مثال از attribute های microdata برای نمایش داده‌های ساختاریافته یک محصول استفاده می‌کند، به صورت زیر:

```markdown
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
        سبک‌تر از سندان کلاسیک ACME؛ سندان Executive Anvil برای مسافرِ کاری که دنبال وسیله‌ای برای انداختن از ارتفاع است، عالی است.
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
> ابزار «Structured Data Testing Tool» گوگل، ابزاری کاربردی برای استخراج ساختارهای microdata از HTML است. می‌توانید همین HTML که در بالا نشان داده شده را داخل آن امتحان کنید.

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
</div>
```

```markdown
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
```

#### نتیجه

## مشخصات

## همچنین ببینید

- [سایر ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes)
- سایر ویژگی‌های سراسری مرتبط با ریزداده (microdata):
  - [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - [`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref)
  - [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)