---
title: "Node: previousSibling property"
short-title: previousSibling
slug: Web/API/Node/previousSibling
page-type: web-api-instance-property
browser-compat: api.Node.previousSibling
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`previousSibling`** در رابط {{domxref("Node")}}، گره‌ای را برمی‌گرداند که بلافاصله قبل از گره مشخص‌شده در فهرست {{domxref("Node.childNodes", "childNodes")}} والد آن قرار دارد، یا اگر گره مشخص‌شده اولین گره در آن فهرست باشد، `null` را برمی‌گرداند.

> [!NOTE]
> مرورگرها برای نمایش فاصله‌های خالی در نشانه‌گذاری منبع، گره‌های متنی را در سند وارد می‌کنند.
> بنابراین ممکن است گره‌ای که مثلاً با استفاده از [`Node.firstChild`](/en-US/docs/Web/API/Node/firstChild)
> یا `Node.previousSibling` به دست می‌آید، به یک گره متنی حاوی فاصله اشاره کند، نه عنصر واقعی‌ای که نویسنده قصد دریافت آن را داشته است.
>
> برای اطلاعات بیشتر، [کار با فاصله‌های خالی در DOM](/en-US/docs/Web/CSS/Guides/Text/Whitespace#working_with_whitespace_in_the_dom) را ببینید.
>
> می‌توانید از [`previousElementSibling`](/en-US/docs/Web/API/Element/previousElementSibling)
> برای دریافت گره عنصر قبلی استفاده کنید (با رد شدن از گره‌های متنی و هر گره غیرعنصر دیگری).
>
> برای پیمایش در جهت مخالف در فهرست گره‌های فرزند، از [Node.nextSibling](/en-US/docs/Web/API/Node/nextSibling) استفاده کنید.

## مقدار

یک {{domxref("Node")}} که خواهر/برادر قبلی گره فعلی را نشان می‌دهد، یا اگر وجود نداشته باشد، `null`.

## مثال‌ها

مثال‌های زیر نشان می‌دهند که `previousSibling` چگونه با وجود گره‌های متنی در کنار عناصر و بدون آن‌ها کار می‌کند.

### مثال اول

در این مثال، یک سری عنصر {{HTMLElement("span")}} مستقیماً در کنار یکدیگر قرار دارند و هیچ فاصله‌ای بین آن‌ها نیست.

```html
<span id="b0"></span><span id="b1"></span><span id="b2"></span>
```

```js
document.getElementById("b1").previousSibling; // <span id="b0">
document.getElementById("b2").previousSibling.id; // "b1"
```

### مثال دوم

در این مثال، بین عناصر {{htmlelement("span")}} گره‌های متنی حاوی فاصله (شکست خط) وجود دارد.

```html
<span id="b0"></span>
<span id="b1"></span>
<span id="b2"></span>
```

```js
document.getElementById("b1").previousSibling; // #text
document.getElementById("b1").previousSibling.previousSibling; // <span id="b0">
document.getElementById("b2").previousSibling.previousSibling; // <span id="b1">
document.getElementById("b2").previousSibling; // #text
document.getElementById("b2").previousSibling.id; // undefined
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.nextSibling")}}
- {{domxref("Element.previousElementSibling")}}