---
title: "HTMLInputElement: width property"
short-title: width
slug: Web/API/HTMLInputElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.width
---

{{APIRef("HTML DOM")}}

ویژگی **`width`** در رابط {{DOMxRef("HTMLInputElement")}} عرض یک کنترل را مشخص می‌کند. این ویژگی، صفت [`width`](/en-US/docs/Web/HTML/Reference/Elements/input#width) عنصر {{htmlelement("input")}} را بازتاب می‌دهد.

ویژگی `width` فقط برای نوع [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است. این ویژگی، اندازه افقی ترجیحی دکمه تصویری را بر حسب پیکسل تعریف می‌کند. مقدار ویژگی، عرض [جعبه محتوا](/en-US/docs/Web/CSS/Reference/Values/box-edge#content-box) دکمه رندر شده است. ویژگی‌های مدل جعبه CSS که بر اندازه کنترل تأثیر می‌گذارند، اولویت دارند.

اگر هیچ `width` تنظیم نشده باشد و هیچ ویژگی عرض CSS بر کنترل تأثیر نگذارد، `width` برابر با عرض ذاتی تصویر خواهد بود. اگر تصویر بارگذاری نشده باشد، مقدار برابر با حداکثر عرض ذاتی متن `alt` خواهد بود. اگر عرض مشخص نباشد، `width` برابر با `0` خواهد بود؛ یعنی وقتی هیچ `width` تنظیم نشده، هیچ ابعاد CSS اعمال نشده، هیچ تصویری بارگذاری نشده، و مقدار {{DOMxRef("HTMLInputElement.alt", "alt")}} رشته خالی باشد یا هیچ `src` تنظیم نشده باشد.

## مقدار

یک عدد.

## مثال‌ها

```js
const inputElement = document.getElementById("imageButton");
console.log(inputElement.width);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLInputElement.height")}}
- {{DOMxRef("HTMLInputElement.src")}}
- {{DOMxRef("HTMLInputElement.alt")}}
- {{DOMXref("HTMLButtonElement")}}
- {{HTMLElement("button")}}
- {{HTMLElement("input")}}
- {{HTMLElement("img")}}
- ویژگی CSS {{CSSXRef("inline-size")}}
- ویژگی CSS {{CSSXRef("width")}}
- ویژگی CSS {{CSSXRef("aspect-ratio")}}
- ماژول [اندازه‌گیری جعبه CSS](/en-US/docs/Web/CSS/Guides/Box_sizing)