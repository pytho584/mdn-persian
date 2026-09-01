---
title: "HTMLInputElement: height property"
short-title: height
slug: Web/API/HTMLInputElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.height
---

{{APIRef("HTML DOM")}}

ویژگی **`height`** در رابط {{DOMxRef("HTMLInputElement")}} ارتفاع یک کنترل را مشخص می‌کند. این ویژگی، بازتاب‌دهنده ویژگی [`height`](/en-US/docs/Web/HTML/Reference/Elements/input#height) عنصر {{htmlelement("input")}} است.

ویژگی `height` فقط برای نوع [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است. بُعد عمودی دکمه تصویری را بر حسب پیکسل تعریف می‌کند. اگر ویژگی‌های اندازه‌گذاری CSS روی کنترل اعمال شوند، مقدار این ویژگی، ارتفاع جعبه محتوای کنترل رندر شده است، نه مقدار ویژگی `height`. اگر `height` تنظیم نشده باشد و CSS اندازه کنترل را تحت تأثیر قرار ندهد، مقدار `height` برابر با ارتفاع ذاتی تصویر خواهد بود. اگر تصویر بارگیری نشود، مقدار برابر با ارتفاع متن `alt` خواهد بود. اگر ارتفاع مشخص نباشد، `height` برابر با `0` خواهد بود؛ این حالت وقتی رخ می‌دهد که `height` تنظیم نشده باشد، CSS ارتفاع را تحت تأثیر قرار ندهد، تصویر بارگیری نشود، و یا مقدار {{DOMxRef("HTMLInputElement.alt", "alt")}} رشته خالی باشد یا `src` تنظیم نشده باشد.

## مقدار

یک عدد.

## مثال‌ها

```js
const inputElement = document.getElementById("imageButton");
console.log(inputElement.height);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLInputElement.width")}}
- {{DOMxRef("HTMLInputElement.src")}}
- {{DOMxRef("HTMLInputElement.alt")}}
- {{DOMXref("HTMLButtonElement")}}
- {{HTMLElement("button")}}
- {{HTMLElement("input")}}
- {{HTMLElement("img")}}
- ویژگی CSS {{CSSXRef("inline-size")}}
- ویژگی CSS {{CSSXRef("height")}}
- ویژگی CSS {{CSSXRef("aspect-ratio")}}
- ماژول [CSS box sizing](/en-US/docs/Web/CSS/Guides/Box_sizing)