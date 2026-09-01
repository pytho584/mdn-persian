---
title: "HTMLImageElement: alt property"
short-title: alt
slug: Web/API/HTMLImageElement/alt
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.alt
---

{{APIRef("HTML DOM")}}

ویژگی **`alt`** از رابط {{domxref("HTMLImageElement")}}، متن جایگزین (fallback) را برای نمایش در زمانی‌که تصویر مشخص‌شده توسط عنصر {{HTMLElement("img")}} نمایش داده نمی‌شود، فراهم می‌کند؛ خواه به دلیل خطا، غیرفعال بودن بارگذاری تصاویر توسط کاربر، یا تکمیل نشدن بارگذاری تصویر. این ویژگی منعکس‌کننده ویژگی محتوایی [`alt`](/en-US/docs/Web/HTML/Reference/Elements/img#alt) عنصر `<img>` است.

ارائه متن جایگزین مناسب پیامدهای مهمی برای دسترسی‌پذیری دارد و الزامات ممکن است بسته به هدف تصویر متفاوت باشد. برای اطلاعات بیشتر به مرجع HTML [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#authoring_meaningful_alternate_descriptions) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### تنظیم ویژگی alt

```js
const img = new Image();
img.src = "example.png";
img.alt = "An example picture";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}