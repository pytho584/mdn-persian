---
title: "CSSPseudoElement: pseudo() method"
short-title: pseudo()
slug: Web/API/CSSPseudoElement/pseudo
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSPseudoElement.pseudo
---

{{APIRef}}{{SeeCompatTable}}

متد **`pseudo()`** از رابط {{domxref("CSSPseudoElement")}} یک نمونه‌ی `CSSPseudoElement` برمی‌گرداند که نمایانگر یک [شبه‌عنصر تودرتو](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#nesting_pseudo-elements) خاص است.

## نحو (Syntax)

```js-nolint
pseudo(type)
```

### پارامترها

- `type`
  - : یک رشته که نوع شبه‌عنصری را که باید نمایی از آن برگردانده شود مشخص می‌کند. مقادیر معتبر عبارت‌اند از:
    - {{cssxref("::after")}}
    - {{cssxref("::before")}}
    - {{cssxref("::marker")}}

### مقدار بازگشتی

یک نمونه‌ی آبجکت {{domxref("CSSPseudoElement")}}، یا اگر `type` برابر با یک نوع شبه‌عنصر معتبر نباشد، `null`.

## توضیحات

متد `CSSPseudoElement.pseudo()` برای هدف قرار دادن شبه‌عنصری استفاده می‌شود که به شبه‌عنصر دیگری متصل است، نه مستقیماً به یک عنصر استاندارد DOM. برای مثال، اگر یک شبه‌عنصر `::before` یک نشانگر فهرست تولید کند — که از طریق `::before::marker` قابل انتخاب است — این متد می‌تواند `::marker` تودرتوی داخل آن `::before` را بازیابی کند. شما متد را روی شبه‌عنصر والد فراخوانی کرده و نوع شبه‌عنصر فرزند تودرتو را به عنوان آرگومان ارسال می‌کنید.

به شرطی که پارامتر `type` شامل یک نوع شبه‌عنصر معتبر باشد، `pseudo()` همیشه یک نمونه‌ی `CSSPseudoElement` برمی‌گرداند، حتی اگر آن شبه‌عنصر روی شبه‌عنصر فراخوانی‌شده تولید نشده باشد.

## مثال‌ها

### استفاده‌ی پایه

در این مثال، استفاده‌ی پایه از متد `pseudo()` را نشان می‌دهیم.

#### HTML

ما یک عنصر {{htmlelement("p")}} حاوی متن و یک عنصر {{htmlelement("output")}} برای ثبت خروجی از جاوااسکریپت قرار می‌دهیم.

```html live-sample___basic
<p>New York's hottest club is...</p>
<output></output>
```

#### CSS

ما به شبه‌عنصر {{cssxref("::after")}} عنصر `<p>` مقداری {{cssxref("content")}} می‌دهیم و {{cssxref("display")}} آن را روی `list-item` تنظیم می‌کنیم تا یک `::marker` تولید کند. همچنین چند سبک پایه اعمال می‌کنیم.

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

#### جاوااسکریپت

در اسکریپت خود، ارجاع‌هایی به عناصر `<p>` و `<output>` می‌گیریم و آبجکت‌های `CSSPseudoElement` را از طریق متد `pseudo()` بازیابی می‌کنیم که نمایانگر شبه‌عنصر `::after` عنصر `<p>` و شبه‌عنصر `::marker` شبه‌عنصر `::after` هستند. سپس چند جزئیات از شبه‌عنصر فرزند را در عنصر `<output>` خود ثبت می‌کنیم. همچنین برای مدیریت خطاهای ابتدایی، از ساختار [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) استفاده می‌کنیم تا در مرورگرهای غیرپشتیبانی‌کننده پیام خطا چاپ شود.

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
- {{DOMxRef("CSSPseudoElement.parent")}}
- {{DOMxRef("Element.pseudo()")}}