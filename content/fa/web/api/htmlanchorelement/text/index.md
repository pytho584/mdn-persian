---
title: "HTMLAnchorElement: text property"
short-title: text
slug: Web/API/HTMLAnchorElement/text
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.text
---

{{ApiRef("HTML DOM")}}

ویژگی **`text`** در {{domxref("HTMLAnchorElement")}} متن داخل عنصر را نمایش می‌دهد. این ویژگی همان اطلاعاتی را ارائه می‌دهد که {{domxref("Node.textContent")}} ارائه می‌کند.

## مقدار

یک رشته (string).

## مثال

```html
<a id="exampleLink" href="https://example.com">Example Link</a>
<p class="text"></p>
```

```css
#exampleLink {
  font-size: 1.5rem;
}
```

```js
const anchorElement = document.getElementById("exampleLink");
const pTag = document.querySelector(".text");
pTag.textContent = `Text property: ${anchorElement.text}`;
```

### نتیجه

{{EmbedLiveSample("Example",100,100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLScriptElement.text")}}
- ویژگی {{domxref("HTMLOptionElement.text")}}