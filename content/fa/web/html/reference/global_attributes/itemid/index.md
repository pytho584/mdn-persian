---
title: "itemid HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemid"
translated_by: "n8n + AI"
---

ویژگی سراسری `itemid` یک شناسه منحصربه‌فرد و سراسری برای یک آیتم در قالب microdata فراهم می‌کند.

ویژگی `itemid` فقط روی عنصری قابل تعیین است که دارای ویژگی‌های `itemscope` و `itemtype` باشد. همچنین، `itemid` فقط روی عناصری قابل تعیین است که دارای ویژگی `itemscope` بوده و `itemtype` متناظر آن به واژگانی (vocabulary) اشاره کند یا تعریف کند که از شناسه‌های سراسری پشتیبانی می‌کند.

معنای دقیق یک شناسه سراسری `itemtype` توسط تعریف آن شناسه در واژگان مشخص‌شده ارائه می‌شود. واژگان مشخص می‌کند که آیا چندین آیتم با شناسه سراسری یکسان می‌توانند هم‌زمان وجود داشته باشند و اگر چنین است، آیتم‌های با شناسه یکسان چگونه مدیریت می‌شوند.

> **توجه:** تعریف WHATWG مشخص می‌کند که `itemid` باید یک URL باشد. با این حال، مثال زیر به درستی نشان می‌دهد که ممکن است از یک URN نیز استفاده شود. این ناهماهنگی ممکن است نشان‌دهنده ناقص بودن مشخصات Microdata باشد.

## مثال‌ها

### نمایش داده‌های ساختاریافته برای یک کتاب

این مثال از ویژگی‌های microdata برای نمایش داده‌های ساختاریافته زیر استفاده می‌کند:

- **itemscope** با **itemtype** و **itemid**:
  - `itemtype`: `https://schema.org/Book`
  - `itemid`: `urn:isbn:0-374-22848-5`
- **itemprop**:
  - `title`: "Owls of the Eastern Ice"
  - `author`: "Jonathan C Slaght"
  - `datePublished`: "2020-08-04"

#### HTML

```html
<dl
  itemscope
  itemtype="https://schema.org/Book"
  itemid="urn:isbn:0-374-22848-5<">
  <dt>Title</dt>
  <dd itemprop="title">Owls of the Eastern Ice</dd>
  <dt>Author</dt>
  <dd itemprop="author">Jonathan C Slaght</dd>
  <dt>Publication date</dt>
  <dd>
    <time itemprop="datePublished" datetime="2020-08-04">August 4 2020</time>
  </dd>
</dl>
```

## مشخصات

- [HTML Standard - attr-itemid](https://html.spec.whatwg.org/multipage/microdata.html#attr-itemid)

## همچنین ببینید

- همه [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)
- دیگر ویژگی‌های سراسری مرتبط با microdata:
  - [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - [`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref)
  - [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)
  - [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype)