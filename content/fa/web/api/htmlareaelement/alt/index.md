---
title: "HTMLAreaElement: alt property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLAreaElement/alt"
---

---
title: "HTMLAreaElement: alt property"
short-title: alt
slug: Web/API/HTMLAreaElement/alt
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.alt
---

{{APIRef("HTML DOM")}}

ویژگی **`alt`** از رابط {{DOMxRef("HTMLAreaElement")}} متنِ ابرپیوند را مشخص می‌کند و برچسب متنیِ پیوندِ یک نقشه تصویری (image map) را تعریف می‌کند. این ویژگی، ویژگی [`alt`](/en-US/docs/Web/HTML/Reference/Elements/area#alt) عنصر {{htmlelement("area")}} را بازتاب می‌دهد.

مقدار `alt` باید متنی باشد که وقتی همراه با متن `alt` سایر ابرپیوندهای `<area>` در همان {{htmlelement("map")}} و همچنین متن `alt` خودِ {{htmlelement("img")}} ارائه شود، همان نوع انتخاب را به کاربر بدهد که ابرپیوند در صورت استفاده بدون متن خود، اما با اعمال شکل‌اش روی تصویر، ارائه می‌کرد.

اگر {{htmlelement("area")}} یک پیوند باشد (دارای ویژگی {{DOMXRef("HTMLAreaElement.href", "href")}} باشد)، مقدار ویژگی `alt` باید یک رشته غیرخالی باشد که برچسب پیوند را به‌گونه‌ای مناسب ارائه دهد که گویی تصویر در دسترس نیست. ویژگی `alt` برای یک `<area>` که پیوند است، تنها زمانی می‌تواند خالی باشد که عنصر `<area>` دیگری در همان `<map>` وجود داشته باشد که به همان منبع اشاره کند و ویژگی `alt` غیرخالی داشته باشد.

## مقدار

یک رشته (string).

## مثال‌ها

```js
const areaElement = document.getElementById("imageArea");
console.log(areaElement.alt);
areaElement.alt = "A much better link description";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMXref("HTMLImageElement.alt")}}
- {{DOMXref("HTMLInputElement.alt")}}
- {{DOMXref("HTMLMapElement")}}
- {{HTMLElement("area")}}
- {{HTMLElement("map")}}
- {{HTMLElement("a")}}
- [متن جایگزین خوب، متن جایگزین بد — قابل درک کردن محتوای خود](https://www.wcag.com/blog/good-alt-text-bad-alt-text-making-your-content-perceivable/) در WCAG.com (۲۰۲۱)
- [درخت تصمیم‌گیری برای متن جایگزین](https://www.w3.org/WAI/tutorials/images/decision-tree/) در ابتکار دسترسی‌پذیری وب W3C (WAI)