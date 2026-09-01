---
title: "HTMLButtonElement: interestForElement property"
short-title: interestForElement
slug: Web/API/HTMLButtonElement/interestForElement
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.interestForElement
---

{{ApiRef("HTML DOM")}}{{SeeCompatTable}}{{non-standard_header}}

ویژگی **`interestForElement`** در رابط {{domxref("HTMLButtonElement")}}، عنصر هدفِ یک interest invoker را دریافت یا تنظیم می‌کند؛ در حالتی که عنصر {{htmlelement("button")}} مرتبط، به‌عنوان interest invoker تعیین شده باشد.

برای جزئیات بیشتر، به [ایجاد یک interest invoker](/en-US/docs/Web/API/Popover_API/Using_interest_invokers#creating_an_interest_invoker) مراجعه کنید.

## مقدار

یک نمونه از شیء {{domxref("Element")}}، یا `null` اگر عنصر `<button>` مرتبط عنصر هدف مشخصی نداشته باشد.

## مثال‌ها

### استفاده پایه از `interestForElement`

در این مثال، از ویژگی `interestForElement` عنصر `<button>` استفاده می‌کنیم تا عنصر هدف آن را تنظیم و سپس `tagName` عنصر هدف را بازیابی کنیم. پس از آن، `tagName` در محتوای متنی عنصر `<button>` نمایش داده می‌شود.

#### HTML

یک عنصر `<button>` و یک عنصر `<div>` قرار داده‌ایم. عنصر `<div>` را با افزودن ویژگی `popover` به آن، به یک popover تبدیل می‌کنیم.

```html live-sample___basic-interest-invoker
<button href="#">a button</button>
<div id="mypopover" popover>I am a <code>&lt;div&gt;</code> element.</div>
```

#### جاوااسکریپت

در اسکریپت، ارجاعاتی به عناصر `<button>` و `<div>` می‌گیریم، سپس با قرار دادن ویژگی `interestForElement` عنصر `<button>` برابر با ارجاعی به `<div>`، رابطهٔ میان interest invoker و عنصر هدف را بین آن‌ها برقرار می‌کنیم. سپس محتوای متنی دکمه را برابر رشته‌ای قرار می‌دهیم که حاوی `tagName` عنصر هدف است و از طریق `invoker.interestForElement.tagName` بازیابی شده است.

```js live-sample___basic-interest-invoker
const invoker = document.querySelector("button");
const popover = document.querySelector("div");

invoker.interestForElement = popover;

invoker.textContent = `My target is a ${invoker.interestForElement.tagName} element`;
```

#### نتیجه

نتیجهٔ این مثال به شکل زیر نمایش داده می‌شود:

{{embedlivesample("basic-interest-invoker", "100%", "100")}}

برای نمایش عنصر `<div>`، علاقهٔ خود را به دکمه نشان دهید (مثلاً با نگه‌داشتن نشانگر ماوس روی آن یا دادن فوکوس به آن).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از interest invokerها](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)
- [API Popover](/en-US/docs/Web/API/Popover_API)