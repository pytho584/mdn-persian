---
title: "HTMLAnchorElement: interestForElement property"
short-title: interestForElement
slug: Web/API/HTMLAnchorElement/interestForElement
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.HTMLAnchorElement.interestForElement
---

{{ApiRef("HTML DOM")}}{{SeeCompatTable}}{{non-standard_header}}

ویژگی **`interestForElement`** از رابط {{domxref("HTMLAnchorElement")}}، عنصر هدف یک دعوت‌کنندهٔ علاقه (interest invoker) را دریافت یا تنظیم می‌کند، در مواردی که عنصر {{htmlelement("a")}} مرتبط به عنوان یک دعوت‌کنندهٔ علاقه مشخص شده است.

برای جزئیات بیشتر، به [ایجاد یک دعوت‌کنندهٔ علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers#creating_an_interest_invoker) مراجعه کنید.

## مقدار

یک نمونه از شیء {{domxref("Element")}}، یا `null` اگر عنصر `<a>` مرتبط عنصر هدفی تنظیم نکرده باشد.

## نمونه‌ها

### استفادهٔ پایه از `interestForElement`

در این مثال، از ویژگی `interestForElement` یک عنصر `<a>` برای تنظیم عنصر هدف آن استفاده می‌کنیم و سپس `tagName` آن عنصر را بازیابی می‌کنیم. سپس `tagName` در محتوای متنی عنصر `<a>` چاپ می‌شود.

#### HTML

```html live-sample___basic-interest-invoker
<a href="#">a link</a>
<div id="mypopover" popover>I am a <code>&lt;div&gt;</code> element.</div>
```

#### JavaScript

```js live-sample___basic-interest-invoker
const invoker = document.querySelector("a");
const popover = document.querySelector("div");

invoker.interestForElement = popover;

invoker.textContent = `My target is a ${invoker.interestForElement.tagName} element`;
```

#### نتیجه

نمونه به این صورت نمایش داده می‌شود:

{{embedlivesample("basic-interest-invoker", "100%", "100")}}

تلاش کنید به پیوند علاقه نشان دهید (مثلاً با قرار دادن نشانگر روی آن یا فوکوس کردن) تا `<div>` ظاهر شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از دعوت‌کننده‌های علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)
- [API Popover](/en-US/docs/Web/API/Popover_API)