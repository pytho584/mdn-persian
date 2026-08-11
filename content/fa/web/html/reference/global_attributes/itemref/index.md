---
title: "itemref HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemref"
translated_by: "n8n + AI"
---

ویژگی سراسری HTML **`itemref`** به شما امکان می‌دهد ویژگی‌هایی (properties) را که از نوادگان (descendants) یک عنصر دارای [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope) نیستند، به آن آیتم (item) متصل کنید.

`itemref` فهرستی از شناسه‌های عناصر (element IDs) – نه `itemid`ها – را در جای دیگری از سند مشخص می‌کند که ویژگی‌های اضافی را ارائه می‌دهند.

ویژگی `itemref` فقط روی عناصری قابل استفاده است که ویژگی `itemscope` روی آنها تعیین شده باشد.

> **نکته:** ویژگی `itemref` بخشی از مدل داده‌ای microdata محسوب نمی‌شود. این فقط یک ساختار نحوی (syntactic construct) است تا به نویسندگان کمک کند در صفحاتی که داده‌های مورد نظر از ساختار درختی ساده‌ای پیروی نمی‌کنند، حاشیه‌نویسی (annotation) اضافه کنند. برای مثال، به نویسنده اجازه می‌دهد داده‌های یک جدول را طوری علامت‌گذاری کند که هر ستون یک آیتم مجزا را تعریف کند، در حالی که ویژگی‌ها داخل سلول‌ها باقی می‌مانند.

## مثال‌ها

### نمایش داده‌های ساختاریافته برای یک گروه موسیقی

این مثال از ویژگی‌های microdata برای نمایش داده‌های ساختاریافته زیر (به فرمت [JSON-LD](https://json-ld.org/)) استفاده می‌کند:

```json
{
  "@id": "amanda",
  "name": "Amanda",
  "band": {
    "@id": "b",
    "name": "Jazz Band",
    "size": 12
  }
}
```

#### HTML

```html
<div itemscope id="amanda" itemref="a b"></div>
<p id="a">Name: <span itemprop="name">Amanda</span></p>
<div id="b" itemprop="band" itemscope itemref="c"></div>
<div id="c">
  <p>Band: <span itemprop="name">Jazz Band</span></p>
  <p>Size: <span itemprop="size">12</span> players</p>
</div>
```

#### نتیجه

{{EmbedLiveSample('Representing structured data for a band')}}

## مشخصات

{{Specifications}}

## همچنین ببینید

- [سایر ویژگی‌های سراسری HTML](/en-US/docs/Web/HTML/Reference/Global_attributes)
- سایر ویژگی‌های سراسری مرتبط با microdata:
  - [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)
  - [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype)