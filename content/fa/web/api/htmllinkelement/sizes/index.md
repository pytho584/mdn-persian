---
title: "HTMLLinkElement: sizes property"
---

---
title: "HTMLLinkElement: sizes property"
short-title: sizes
slug: Web/API/HTMLLinkElement/sizes
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.sizes
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`sizes`** در رابط {{domxref("HTMLLinkElement")}} اندازه‌های آیکون‌های رسانه‌های تصویری موجود در منبع را تعریف می‌کند. این ویژگی منعکس‌کنندهٔ صفت [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/link#sizes) عنصر {{HTMLElement("link")}} است؛ صفتی که فهرستی از اندازه‌های جدا شده با فاصله را می‌گیرد، هر یک در قالب `<عرض بر حسب پیکسل>x<ارتفاع بر حسب پیکسل>` یا کلیدواژهٔ `any`.

این ویژگی تنها زمانی مرتبط است که {{domxref("HTMLLinkElement.rel", "rel")}} برابر با `icon` یا نوعی غیراستاندارد مانند `apple-touch-icon` باشد.

## مقدار

یک شیء {{domxref("DOMTokenList")}}.

اگرچه خود ویژگی `sizes` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، همچنان می‌توانید مستقیماً به ویژگی `sizes` مقدار بدهید؛ این کار معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```html
<link rel="icon" sizes="72x72 114x114" href="smallish.ico" />
```

```js
const link = document.querySelector("[rel=icon],[rel=apple-touch-icon]");
console.dir(link.sizes); /* output:
  DOMTokenList [ "72x72", "114x114" ]
    0: "72x72"
    1: "114x114"
    length: 2
    value: "72x72 114x114"
  */
console.log(link.sizes.value); // output: '72x72 114x114'
console.log(link.sizes.length); // output: 2'
console.log(link.sizes[0]); // output: '72x72'
console.log(link.sizes[1]); // output: '114x114'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLLinkElement.rel")}}
- {{domxref("HTMLLinkElement.relList")}}
- {{domxref("HTMLLinkElement.type")}}
- {{domxref("HTMLLinkElement.href")}}
- {{HTMLElement("link")}}
- صفت [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel)