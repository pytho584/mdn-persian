---
title: "Document: images property"
---

---
title: "Document: images property"
short-title: images
slug: Web/API/Document/images
page-type: web-api-instance-property
browser-compat: api.Document.images
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`images`** در رابط {{domxref("Document")}} یک [مجموعه](/en-US/docs/Web/API/HTMLCollection) از [تصویرها](/en-US/docs/Web/API/HTMLImageElement) موجود در سند HTML فعلی را برمی‌گرداند.

## مقدار

یک {{domxref("HTMLCollection")}} که فهرستی زنده از همهٔ تصویرهای موجود در سند فعلی فراهم می‌کند. هر ورودی در این مجموعه یک {{domxref("HTMLImageElement")}} است که یک عنصر تصویر را نمایش می‌دهد.

## نکات استفاده

برای دسترسی به آیتم‌های مجموعه، می‌توانید از نحو آرایه‌ای جاوااسکریپت یا از متد {{domxref("HTMLCollection.item", "item()")}} روی مجموعهٔ برگشتی استفاده کنید. دو روش زیر معادل یکدیگرند:

```js
firstImage = imageCollection.item(0);

firstImage = imageCollection[0];
```

## مثال‌ها

این مثال فهرست تصویرها را می‌پیماید و تصویرهایی را پیدا می‌کند که `"banner.gif"` نام دارند.

```js
for (const image of document.images) {
  if (image.src === "banner.gif") {
    console.log("Found the banner");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}