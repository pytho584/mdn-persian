---
title: "HTMLLinkElement: hreflang property"
short-title: hreflang
slug: Web/API/HTMLLinkElement/hreflang
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.hreflang
---

{{APIRef("HTML DOM")}}

ویژگی **`hreflang`** در رابط {{domxref("HTMLLinkElement")}} برای نشان‌دادن زبان و هدف جغرافیایی یک صفحه استفاده می‌شود. این نشانه می‌تواند توسط مرورگرها برای انتخاب صفحه مناسب‌تر یا بهبود {{Glossary("SEO")}} استفاده شود.

این ویژگی منعکس‌کنندهٔ صفت `hreflang` عنصر {{HTMLElement("link")}} است و اگر هیچ صفت `hreflang`ای وجود نداشته باشد، رشتهٔ خالی (`""`) خواهد بود.

## مقدار

یک رشته که شامل یک برچسب زبان است، یا اگر هیچ صفت `hreflang`ای وجود نداشته باشد، رشتهٔ خالی (`""`).

## مثال

```html
<link
  rel="alternate"
  href="www.example.com/fr/html"
  hreflang="fr"
  type="text/html"
  title="French HTML" />
<p class="tag"></p>
```

```css
.tag {
  margin-left: 20px;
  font-weight: bold;
  font-size: 24px;
}
```

```js
const myLink = document.querySelector("link");
const pTag = document.querySelector(".tag");
pTag.textContent = myLink.hreflang;
```

## نتایج

{{EmbedLiveSample("Example",100,100)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLAnchorElement.hreflang")}}