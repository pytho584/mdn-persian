---
title: "HTMLImageElement: name property"
short-title: name
slug: Web/API/HTMLImageElement/name
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLImageElement.name
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی «منسوخ‌شده» **`name`** در رابط {{domxref("HTMLImageElement")}} نامی برای عنصر تعیین می‌کند. این ویژگی، ویژگی محتوایی [`name`](/en-US/docs/Web/HTML/Reference/Elements/img#name) عنصر `<img>` را منعکس می‌کند. این ویژگی با ویژگی {{domxref("Element.id", "id")}} که روی همه عناصر موجود است جایگزین شده و فقط به دلایل سازگاری نگه داشته شده است.

## مقدار

یک رشته (string) که نامی برای ارجاع به تصویر فراهم می‌کند.

## مثال‌ها

### تنظیم ویژگی name

```js
const img = new Image();
img.src = "example.png";
img.alt = "An example picture";
img.name = "example-img";
```

به جای این کار، ویژگی `id` را تنظیم کنید:

```js
img.id = "example-img";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}