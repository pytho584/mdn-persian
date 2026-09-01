---
title: "FragmentDirective"
---

---
title: FragmentDirective
slug: Web/API/FragmentDirective
page-type: web-api-interface
browser-compat: api.FragmentDirective
---

{{APIRef("URL Fragment Text Directives")}}

رابط **`FragmentDirective`** یک شیء در معرض است که به کد اجازه می‌دهد بررسی کند که آیا مرورگر از [تکه‌های متنی](/en-US/docs/Web/URI/Reference/Fragment/Text_fragments) پشتیبانی می‌کند یا خیر.

از طریق ویژگی {{domxref("Document.fragmentDirective")}} قابل دسترسی است.

## ویژگی‌های نمونه

هیچ.

## روش‌های نمونه

هیچ.

## مثال‌ها

### بررسی پشتیبانی از تکه‌های متنی

کد زیر با بررسی تعریف‌شدن {{domxref("Document.fragmentDirective")}} مشخص می‌کند که آیا مرورگر شما از تکه‌های متنی پشتیبانی می‌کند یا خیر و آن را در خروجی ثبت می‌کند.
توجه داشته باشید که این شیء خالی است و در حال حاضر عمدتاً برای تشخیص ویژگی در نظر گرفته شده است.
در آینده، ممکن است اطلاعات دیگری را شامل شود.

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

```js
if (document.fragmentDirective) {
  log("Your browser supports text fragments.");
} else {
  log("Text fragments are not supported in your browser.");
}
```

{{EmbedLiveSample("Checking if text fragments are supported","100%","30px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("::target-text")}}