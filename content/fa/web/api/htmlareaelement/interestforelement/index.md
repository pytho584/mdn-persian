---
title: "HTMLAreaElement: interestForElement property"
---

---
title: "HTMLAreaElement: interestForElement property"
short-title: interestForElement
slug: Web/API/HTMLAreaElement/interestForElement
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.HTMLAreaElement.interestForElement
---

{{ApiRef("HTML DOM")}}{{SeeCompatTable}}{{non-standard_header}}

ویژگی **`interestForElement`** از رابط {{domxref("HTMLAreaElement")}}، عنصر هدف یک فراخوانندهٔ علاقه (interest invoker) را در مواردی که عنصر {{htmlelement("area")}} مرتبط به‌عنوان فراخوانندهٔ علاقه مشخص شده است، دریافت یا تنظیم می‌کند.

برای جزئیات بیشتر، به [ایجاد یک فراخوانندهٔ علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers#creating_an_interest_invoker) مراجعه کنید.

## Value

یک نمونهٔ شیء {{domxref("Element")}}، یا `null` در صورتی که عنصر `<area>` مرتبط، عنصر هدفی برایش تنظیم نشده باشد.

## Examples

### استفادهٔ پایه از `interestForElement`

در این مثال، از ویژگی `interestForElement` یک عنصر `<area>` برای تنظیم عنصر هدف آن استفاده می‌کنیم و سپس `tagName` عنصر هدف را بازیابی می‌کنیم. سپس `tagName` در محتوای متنی عنصر `<area>` چاپ می‌شود.

#### HTML

یک عنصر `<area>` و یک عنصر `<div>` قرار می‌دهیم. عنصر `<div>` را با قرار دادن یک ویژگی `popover` روی آن به یک popover تبدیل می‌کنیم.

```html live-sample___basic-interest-invoker
<map name="example-map" id="example-map">
  <area href="#" shape="default" alt="Example area" />
</map>
<div id="mypopover" popover>I am a <code>&lt;div&gt;</code> element.</div>
```

```css hidden live-sample___basic-interest-invoker
map {
  width: 200px;
  height: 100px;
  background-color: pink;
  padding: 5px;
}
```

#### JavaScript

در اسکریپت، ارجاع‌هایی به عناصر `<area>` و `<div>` می‌گیریم. سپس با قرار دادن ویژگی `interestForElement` عنصر `<area>` برابر با ارجاعی به `<div>`، یک رابطهٔ فراخوانندهٔ علاقه-هدف بین `<area>` و `<div>` برقرار می‌کنیم. سپس محتوای متنی عنصر `<area>` را برابر با رشته‌ای قرار می‌دهیم که شامل `tagName` عنصر هدف است و از طریق `invoker.interestForElement.tagName` به دست آمده است.

```js live-sample___basic-interest-invoker
const invoker = document.querySelector("area");
const popover = document.querySelector("div");

invoker.interestForElement = popover;

invoker.textContent = `My target is a ${invoker.interestForElement.tagName} element`;
```

#### نتیجه

مثال به این شکل نمایش داده می‌شود:

{{embedlivesample("basic-interest-invoker", "100%", "100")}}

برای ظاهر شدن `<div>`، به ناحیهٔ `<area>` علاقه نشان دهید (مثلاً با نشانگر روی آن بروید یا آن را فوکوس کنید).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از فراخواننده‌های علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)
- [API Popover](/en-US/docs/Web/API/Popover_API)
