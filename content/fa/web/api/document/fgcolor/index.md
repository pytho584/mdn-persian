---
title: "Document: fgColor property"
---

---
title: "Document: fgColor property"
short-title: fgColor
slug: Web/API/Document/fgColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.fgColor
---

{{APIRef("DOM")}}{{Deprecated_header}}

**`fgColor`** مقدار رنگ پیشزمینه (یا رنگ متن) سند جاری را میخواند و تنظیم میکند.

## مقدار

رشتهای که رنگ را بهصورت یک کلمه (مثلاً `"red"`) یا مقدار هگزادسیمال (مثلاً `"#ff0000"`) نشان میدهد.

## مثالها

```js
document.fgColor = "white";
document.bgColor = "darkblue";
```

## یادداشتها

مقدار پیشفرض این ویژگی در Mozilla Firefox سیاه است (`#000000` بهصورت هگزادسیمال).

`document.fgColor` در [مشخصات HTML](https://html.spec.whatwg.org/multipage/obsolete.html#dom-document-fgcolor) منسوخ شدهاست. جایگزین توصیهشده، ویژگی CSS {{Cssxref("color")}} است (مثلاً `document.body.style.color = "red"`).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}