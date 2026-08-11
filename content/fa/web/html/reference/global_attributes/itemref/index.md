---
title: "itemref HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemref"
translated_by: "n8n + AI"
---

ویژگی‌هایی که فرزندِ مستقیمِ عنصری با attribute `itemscope` نیستند، می‌توانند با استفاده از **`itemref`** که یک [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) است، به یک آیتم مرتبط شوند.

`itemref` فهرستی از `id` عناصر (نه `itemid`ها) را در جای دیگری از سند فراهم می‌کند تا ویژگی‌های اضافی را شامل شود.

attribute `itemref` فقط روی عناصری قابل استفاده است که `itemscope` داشته باشند.

> [!NOTE]
> `itemref` بخشی از مدل داده‌ی microdata نیست. این صرفاً یک ساختار نحوی است که به نویسندگان کمک می‌کند تا داده‌هایی را که الگوی درختی مناسبی ندارند، در صفحه نشانه‌گذاری کنند. مثلاً امکان نشانه‌گذاری داده‌ها در یک جدول را فراهم می‌کند، به‌طوری که هر ستون یک آیتم جداگانه تعریف کند و ویژگی‌ها در سلول‌ها باقی بمانند.

## مثال‌ها

### نمایش داده‌های ساختاریافته برای یک گروه موسیقی

این مثال از attributeهای microdata برای نمایش داده‌های ساختاریافته‌ی زیر (در قالب [JSON-LD](https://json-ld.org/)) استفاده می‌کند:

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

- [سایر global attributeها](/en-US/docs/Web/HTML/Reference/Global_attributes)
- سایر global attributeهای مرتبط با microdata:
  - [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)
  - [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype)