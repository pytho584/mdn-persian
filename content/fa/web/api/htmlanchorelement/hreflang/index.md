---
title: "HTMLAnchorElement: hreflang property"
short-title: hreflang
slug: Web/API/HTMLAnchorElement/hreflang
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.hreflang
---

{{ApiRef("HTML DOM")}}

ویژگی **`hreflang`** از رابط {{domxref("HTMLAnchorElement")}} یک رشته است که زبان منبع پیوند‌شده را مشخص می‌کند.

این ویژگی منعکس‌کنندهٔ ویژگی `hreflang` عنصر {{HTMLElement("a")}} است و در صورت نبودن عنصر `hreflang`، رشتهٔ خالی (`""`) خواهد بود.

مرورگرهای وب و موتورهای جستجو ممکن است از این اطلاعات برای درک بهتر زبان محتوای پیوند‌شده استفاده کنند، اما الزامی به پیروی از آن ندارند. مقدار ارائه‌شده برای ویژگی `hreflang` از قالب {{glossary("BCP 47 language tag", "برچسب زبان BCP 47")}} پیروی می‌کند. در غیر این صورت، نادیده گرفته می‌شود.

مرورگرهای وب پس از واکشی منبع پیوند‌شده صرفاً به ویژگی `hreflang` متکی نیستند. در عوض، آنها از اطلاعات زبان مستقیماً مرتبط با منبع (مثلاً از طریق هدرهای HTTP) برای تعیین زبان آن استفاده می‌کنند.

## مقدار

یک رشته که شامل یک برچسب زبان است، یا در صورت نبودن عنصر `hreflang`، رشتهٔ خالی (`""`).

## مثال

```html
<a id="exampleLink" href="https://example.com" hreflang="en-IN">Example Link</a>
<p class="hreflang"></p>
```

```css
#exampleLink {
  font-size: 1.5rem;
}
```

```js
const anchorElement = document.getElementById("exampleLink");
const pTag = document.querySelector(".hreflang");
console.log(anchorElement.hreflang); // Outputs: "en-IN"
pTag.textContent = anchorElement.hreflang;
```

## نتیجه

{{EmbedLiveSample("Example",100,100)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLLinkElement.hreflang")}}