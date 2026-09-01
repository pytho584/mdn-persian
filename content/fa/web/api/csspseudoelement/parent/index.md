---
title: "CSSPseudoElement: parent property"
short-title: parent
slug: Web/API/CSSPseudoElement/parent
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSPseudoElement.parent
---

{{APIRef}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`parent`** در رابط {{DOMxRef("CSSPseudoElement")}} ارجاعی به عنصر مبدأ بلافصل شبه‌المان برمی‌گرداند؛ این عنصر می‌تواند یک {{DOMxRef("Element")}} یا در مورد [شبه‌المان تودرتو](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#nesting_pseudo-elements) یک `CSSPseudoElement` باشد.

این رفتار با خاصیت {{DOMxRef("CSSPseudoElement.element")}} تفاوت دارد که همیشه یک `Element` برمی‌گرداند: ارجاعی به عنصر مبدأ نهایی شبه‌المان.

## مقدار

یک {{DOMxRef("Element")}} یا {{DOMxRef("CSSPseudoElement")}} که والد بلافصل شبه‌المان را نشان می‌دهد.

## مثال‌ها

### استفاده پایه

در این مثال، تفاوت بین خاصیت‌های `parent` و {{DOMxRef("CSSPseudoElement.element", "element")}} را نشان می‌دهیم.

#### HTML

یک عنصر {{htmlelement("p")}} حاوی متن و یک عنصر {{htmlelement("output")}} برای ثبت خروجی جاوااسکریپت اضافه می‌کنیم.

```html live-sample___basic
<p>New York's hottest club is...</p>
<output></output>
```

#### CSS

به شبه‌المان {{cssxref("::after")}} عنصر `<p>` یک مقدار {{cssxref("content")}} می‌دهیم و {{cssxref("display")}} آن را روی `list-item` تنظیم می‌کنیم تا یک `::marker` تولید کند. همچنین چند استایل پایه اعمال می‌کنیم.

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
  display: list-item;
}

p::after::marker {
  content: "🔹";
}
```

#### JavaScript

در اسکریپت خود، ارجاع‌هایی به عناصر `<p>` و `<output>` می‌گیریم و اشیاء `CSSPseudoElement` را از طریق متد `pseudo()` بازیابی می‌کنیم که شبه‌المان `::after` عنصر `<p>` و نیز شبه‌المان `::marker` مربوط به آن را نشان می‌دهند. سپس جزئیاتی از شبه‌المان فرزند را در عنصر `<output>` ثبت می‌کنیم. همچنین با استفاده از ساختار [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) مدیریت خطای ابتدایی اضافه کرده‌ایم تا در مرورگرهای غیرپشتیبان پیام خطا چاپ شود.

```js live-sample___basic
const pElem = document.querySelector("p");
const output = document.querySelector("output");

try {
  const pseudoElem = pElem.pseudo("::after");
  const pseudoPseudoElem = pseudoElem.pseudo("::marker");
  output.textContent = `${pseudoPseudoElem.type} pseudo-element. Parent: ${pseudoPseudoElem.parent.type}. Ultimate originating element: <${pseudoPseudoElem.element.tagName.toLowerCase()}>`;
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

- {{DOMxRef("CSSPseudoElement.element")}}
- {{DOMxRef("CSSPseudoElement.pseudo()")}}
- {{DOMxRef("Element.pseudo()")}}