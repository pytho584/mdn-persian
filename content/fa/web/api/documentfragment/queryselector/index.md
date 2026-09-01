---
title: "DocumentFragment: querySelector() method"
short-title: querySelector()
slug: Web/API/DocumentFragment/querySelector
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.querySelector
---

{{ApiRef("DOM")}}

متد **`DocumentFragment.querySelector()`** نخستین عنصری را بازمی‌گرداند که با مجموعه‌ی انتخابگرهای داده‌شده مطابقت دارد، یا در صورت نبودِ هیچ تطابقی، مقدار `null` را برمی‌گرداند. این جستجو درون {{domxref("DocumentFragment")}} و با استفاده از پیمایش پیش‌ترتیبی عمق‌اول (depth-first pre-order) روی گره‌های سند انجام می‌شود.

اگر انتخابگر با یک شناسه (ID) مطابقت داشته باشد و این شناسه چند بار به‌طور نادرست در سند استفاده شده باشد، این متد نخستین عنصر منطبق را بازمی‌گرداند.

اگر انتخابگرهای مشخص‌شده در پارامتر نامعتبر باشند، یک {{domxref("DOMException")}} با مقدار `SYNTAX_ERR` پرتاب می‌شود.

## نحو

```js-nolint
querySelector(selectors)
```

### پارامترها

- `selectors`
  - : رشته‌ای شامل یک یا چند انتخابگر CSS که با کاما از هم جدا شده‌اند.

### مقدار بازگشتی

یک شیء {{domxref("Element")}} که نخستین عنصر منطبق با مجموعه‌ی [انتخابگرهای CSS](/en-US/docs/Web/CSS/Guides/Selectors) مشخص‌شده را نشان می‌دهد. اگر هیچ تطابقی وجود نداشته باشد، `null` بازگردانده می‌شود.

## مثال‌ها

### مثال ابتدایی

در این مثال ابتدایی، نخستین عنصر درون {{domxref("DocumentFragment")}} که کلاس `myclass` را دارد بازگردانده می‌شود:

```js
const el = documentfragment.querySelector(".myclass");
```

### نحو CSS و آرگومان متد

آرگومان رشته‌ای که به `querySelector` داده می‌شود باید از نحو CSS پیروی کند. برای مطابقت با شناسه‌ها یا انتخابگرهایی که از نحو CSS پیروی نمی‌کنند (مثلاً استفاده‌ی نادرست از نقطه‌ویرگول یا فاصله)، الزامی است که کاراکتر نامعتبر را با دو بک‌اسلش escape کنید:

```html
<div id="foo\bar"></div>
<div id="foo:bar"></div>
```

```js
document.querySelector("#foo\bar"); // Does not match anything
document.querySelector("#foo\\\\bar"); // Match the first div
document.querySelector("#foo:bar"); // Does not match anything
document.querySelector("#foo\\:bar"); // Match the second div
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("DocumentFragment")}} که این متد به آن تعلق دارد.