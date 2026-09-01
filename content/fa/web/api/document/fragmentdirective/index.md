---
title: "Document: fragmentDirective property"
short-title: fragmentDirective
slug: Web/API/Document/fragmentDirective
page-type: web-api-instance-property
browser-compat: api.Document.fragmentDirective
---

{{APIRef("URL Fragment Text Directives")}}

ویژگی فقط‌خواندنی **`fragmentDirective`** در رابط {{domxref("Document")}}، شیء {{domxref("FragmentDirective")}} مربوط به سند فعلی را برمی‌گرداند.

## مقدار

یک شیء {{domxref("FragmentDirective")}}.

## مثال‌ها

### بررسی پشتیبانی از متن‌قطعه‌ها (text fragments)

کد زیر با بررسی وجود شیء، مشخص می‌کند که آیا مرورگر شما از متن‌قطعه‌ها پشتیبانی می‌کند یا خیر.
توجه داشته باشید که این شیء خالی است و در حال حاضر عمدتاً برای تشخیص ویژگی (feature detection) در نظر گرفته شده است.
در آینده ممکن است اطلاعات دیگری نیز در بر داشته باشد.

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

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [متن‌قطعه‌ها (Text fragments)](/en-US/docs/Web/URI/Reference/Fragment/Text_fragments)
- {{cssxref("::target-text")}}