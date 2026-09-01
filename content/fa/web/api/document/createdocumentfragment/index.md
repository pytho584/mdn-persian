---
title: "Document: createDocumentFragment() method"
short-title: createDocumentFragment()
slug: Web/API/Document/createDocumentFragment
page-type: web-api-instance-method
browser-compat: api.Document.createDocumentFragment
---

{{APIRef("DOM WHATWG")}}

یک {{domxref("DocumentFragment")}} خالی جدید ایجاد می‌کند که
می‌توان گره‌های DOM را به آن اضافه کرد تا یک درخت DOM خارج از صفحه (offscreen) بسازیم.

## Syntax

```js-nolint
createDocumentFragment()
```

### Parameters

هیچ‌کدام.

### Return value

یک شیء {{domxref("DocumentFragment")}} تازه ایجاد شده و خالی که آماده است
گره‌ها در آن درج شوند.

## Usage notes

اشیاء `DocumentFragment` از نوع {{domxref("Node")}} در DOM هستند که هرگز بخشی
از درخت اصلی DOM نیستند. کاربرد معمول این است که یک document fragment ایجاد کنید،
عناصر را به آن اضافه کنید و سپس document fragment را به درخت DOM اضافه کنید.
در درخت DOM، document fragment با تمام فرزندانش جایگزین می‌شود.

از آنجا که document fragment در _حافظه_ است و بخشی از درخت اصلی DOM نیست،
استفاده از document fragmentها می‌تواند در برخی موتورهای قدیمی‌تر
[عملکرد بهتری](https://johnresig.com/blog/dom-documentfragments/) به همراه داشته باشد.

همچنین می‌توانید از سازنده `DocumentFragment` برای ایجاد یک fragment جدید استفاده کنید:

```js
const fragment = new DocumentFragment();
```

## Examples

این مثال فهرستی از مرورگرهای اصلی وب را در یک `DocumentFragment` ایجاد می‌کند،
سپس زیردرخت DOM جدید را برای نمایش به سند اضافه می‌کند.

### HTML

```html
<ul id="ul"></ul>
```

### JavaScript

```js
const element = document.getElementById("ul"); // فرض بر این است که ul وجود دارد
const fragment = document.createDocumentFragment();
const browsers = ["Firefox", "Chrome", "Opera", "Safari"];

browsers.forEach((browser) => {
  const li = document.createElement("li");
  li.textContent = browser;
  fragment.appendChild(li);
});

element.appendChild(fragment);
```

### Result

{{EmbedLiveSample("Examples", 600, 140)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DOMImplementation.createDocument", "document.implementation.createDocument()")}}
- {{domxref("documentFragment")}}