```
---
title: "HTMLImageElement: decoding property"
short-title: decoding
slug: Web/API/HTMLImageElement/decoding
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.decoding
---

{{APIRef("HTML DOM")}}

خصوصیت `decoding` در رابط (interface) `HTMLImageElement` به مرورگر راهنمایی میدهد که تصویر را چگونه رمزگشایی کند. بهطور دقیقتر، اینکه آیا باید قبل از بهروزرسانی سایر محتواها منتظر رمزگشایی تصویر بماند یا نه. این خصوصیت منعکسکنندهٔ ویژگی محتوایی (content attribute) `decoding` در عنصر `<img>` است.

## مقدار

یک رشته که مقدار آن یکی از `sync`، `async` یا `auto` است. برای آشنایی با معنای آنها، به مستندات [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#decoding) در HTML مراجعه کنید.

## مثالها

در مثال زیر، احتمالاً در حالی که تصویر در حال دانلود است، یک تصویر خالی روی صفحه نمایش داده میشود. تنظیم `decoding` نمیتواند از این اتفاق جلوگیری کند.

```js
const img = new Image();
img.decoding = "sync";
img.src = "img/logo.png";
document.body.appendChild(img);
```

درج یک تصویر پس از دانلود میتواند خصوصیت `decoding` را مرتبطتر کند:

```js
async function loadImage(url, elem) {
  return new Promise((resolve, reject) => {
    elem.onload = () => resolve(elem);
    elem.onerror = reject;
    elem.src = url;
  });
}

const img = new Image();
await loadImage("img/logo.png", img);
// Using `sync` can ensure other content is only updated with the image
img.decoding = "sync";
document.body.appendChild(img);
const p = document.createElement("p");
p.textContent = "Image is fully loaded!";
document.body.appendChild(p);
```

با این حال، راهحل بهتر استفاده از متد {{domxref("HTMLImageElement.decode()")}} برای حل این مشکل است. این متد راهی برای رمزگشایی ناهمگام (async) تصویر فراهم میکند و درج آن در DOM را تا زمان تکمیل دانلود و رمزگشایی به تأخیر میاندازد؛ بنابراین از مشکل تصویر خالی که در بالا ذکر شد جلوگیری میکند. این روش بهویژه زمانی مفید است که بخواهید بهصورت پویا یک تصویر موجود را با تصویر جدید جایگزین کنید و همچنین از متوقف شدن رندرهای نامرتبط خارج از این کد در حین رمزگشایی تصویر جلوگیری میکند.

استفاده از `img.decoding = "async"` ممکن است در صورتی که زمان رمزگشایی طولانی باشد، از توقف نمایش سایر محتواها جلوگیری کند:

```js
const img = new Image();
img.decoding = "async";
img.src = "img/logo.png";
document.body.appendChild(img);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- متد {{domxref("HTMLImageElement.decode()")}}
- ویژگی `decoding` عنصر {{htmlelement("img")}}
- [ویژگی رمزگشایی تصویر واقعاً چه کاری انجام میدهد؟](https://www.tunetheweb.com/blog/what-does-the-image-decoding-attribute-actually-do/) در tunetheweb.com (2023)
```