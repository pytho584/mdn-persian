---
title: "Element: pseudo() method"
short-title: pseudo()
slug: Web/API/Element/pseudo
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Element.pseudo
---

{{SeeCompatTable}}

{{APIRef("DOM")}}

متد **`pseudo()`** در رابط {{domxref("Element")}} یک شیء {{domxref("CSSPseudoElement")}} برمی‌گرداند که نمایانگر [شبه‌عنصر](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) [CSS](/en-US/docs/Web/CSS) از نوع مشخص‌شده و مرتبط با عنصر است.

به شرطی که پارامتر `type` شامل یک نوع شبه‌عنصر معتبر باشد، `pseudo()` همیشه یک نمونه از `CSSPseudoElement` برمی‌گرداند، حتی اگر آن شبه‌عنصر روی عنصر فراخوانی‌شده تولید نشده باشد.

## نحو (Syntax)

```js-nolint
pseudo(type)
```

### پارامترها

- `type`
  - : یک رشته (string) که نوع شبه‌عنصری را که می‌خواهید نمایشی از آن برگردانده شود مشخص می‌کند. مقادیر معتبر عبارت‌اند از:
    - {{cssxref("::after")}}
    - {{cssxref("::before")}}
    - {{cssxref("::marker")}}

### مقدار برگشتی

یک نمونه از شیء {{domxref("CSSPseudoElement")}}، یا اگر `type` برابر با یک نوع شبه‌عنصر معتبر نباشد، `null` برمی‌گرداند.

## مثال‌ها

### استفاده پایه

در این مثال، استفاده پایه از متد `pseudo()` را نشان می‌دهیم.

#### HTML

یک عنصر {{htmlelement("p")}} شامل متن و یک عنصر {{htmlelement("output")}} برای ثبت خروجی جاوااسکریپت قرار می‌دهیم.

```html live-sample___basic
<p>New York's hottest club is...</p>
<output></output>
```

#### CSS

به شبه‌عنصر {{cssxref("::after")}} عنصر `<p>` یک {{cssxref("content")}} می‌دهیم و چند استایل پایه به هر دو اعمال می‌کنیم.

```css hidden live-sample___basic
body {
  width: 80%;
  margin: 0 auto;
}
```

```css live-sample___basic
p {
  background-color: violet;
  padding: 20px;
}

p::after {
  content: "Crease";
  background-color: cadetblue;
  padding: 20px;
}
```

#### جاوااسکریپت

در اسکریپت خود، ارجاع‌هایی به عناصر `<p>` و `<output>` می‌گیریم و یک `CSSPseudoElement` که نمایانگر شبه‌عنصر `::after` عنصر `<p>` است را از طریق متد `pseudo()` دریافت می‌کنیم. سپس برخی جزئیات شبه‌عنصر را در عنصر `<output>` ثبت می‌کنیم. همچنین یک مدیریت خطای ابتدایی با ساختار [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) اضافه می‌کنیم تا در مرورگرهای غیرپشتیبان خطا چاپ شود.

```js live-sample___basic
const pElem = document.querySelector("p");
const output = document.querySelector("output");

try {
  const pseudoElem = pElem.pseudo("::after");
  output.textContent = `${pseudoElem.type} pseudo-element. Parent: <${pseudoElem.parent.tagName.toLowerCase()}>`;
} catch (e) {
  output.textContent = `Your browser doesn't support CSSPseudoElement and/or the pseudo() method: ${e}`;
}
```

#### نتیجه

{{embedlivesample("basic", "100%", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("CSSPseudoElement.pseudo()")}}