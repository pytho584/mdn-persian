---
title: "HTMLBaseElement: خاصیت href"
short-title: href
slug: Web/API/HTMLBaseElement/href
page-type: web-api-instance-property
browser-compat: api.HTMLBaseElement.href
---

{{APIRef("HTML DOM")}}

خاصیت **`href`** از رابط {{domxref("HTMLBaseElement")}} یک رشته را شامل می‌شود که URL مورد استفاده به عنوان پایه برای [نشانی‌های نسبی (relative URLs)](/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL#absolute_urls_vs._relative_urls) است.

این خاصیت منعکس‌کنندهٔ ویژگی `href` عنصر {{HTMLElement("base")}} است.

## مقدار

یک رشته که شامل یک URL است، یا رشتهٔ خالی (`""`) اگر عنصر `<base>` متناظر دارای ویژگی `href` نباشد.

## مثال‌ها

### HTML همراه با URL پایه

این مثال نشان می‌دهد که ویژگی `href` در `<base>` در خاصیت `href` مربوط به `HTMLBaseElement` منعکس می‌شود.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = text;
}
```

```css hidden
#log {
  height: 20px;
}
```

#### HTML

```html
<base href="https://developer.mozilla.org/example" />
```

#### JavaScript

```js
const base = document.getElementsByTagName("base")[0];
log(`base.href="${base.href}"`);
```

#### نتیجه

{{EmbedLiveSample('HTML with base URL', '100','50px')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}