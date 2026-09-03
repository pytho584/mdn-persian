---
title: "Node: nextSibling property"
short-title: nextSibling
slug: Web/API/Node/nextSibling
page-type: web-api-instance-property
browser-compat: api.Node.nextSibling
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`nextSibling`** در رابط {{domxref("Node")}}، گره‌ای را برمی‌گرداند که بلافاصله پس از گره مشخص‌شده در {{domxref("Node.childNodes","childNodes")}} والد قرار دارد. اگر گره مشخص‌شده آخرین فرزند عنصر والد باشد، مقدار `null` برگردانده می‌شود.

> [!NOTE]
> مرورگرها برای نمایش فاصله‌های خالی (whitespace) در نشانه‌گذاری منبع، گره‌های {{domxref("Text")}} را در سند درج می‌کنند.
> بنابراین گره‌ای که مثلاً با استفاده از [`Node.firstChild`](/en-US/docs/Web/API/Node/firstChild)
> یا [`Node.previousSibling`](/en-US/docs/Web/API/Node/previousSibling)
> به دست می‌آید ممکن است به یک گره متنی حاوی فاصله اشاره کند، نه به عنصر واقعی‌ای که نویسنده قصد دریافت آن را داشته است.
>
> بخش [کار با فاصله‌های خالی در DOM](/en-US/docs/Web/CSS/Guides/Text/Whitespace#working_with_whitespace_in_the_dom)
> اطلاعات بیشتری درباره این رفتار ارائه می‌دهد.
>
> می‌توانید از {{domxref("Element.nextElementSibling")}} برای دریافت عنصر بعدی استفاده کنید و از گره‌های فاصله، متن‌های بین عناصر یا کامنت‌ها عبور کنید.
>
> برای پیمایش در جهت مخالف در فهرست گره‌های فرزند، از [Node.previousSibling](/en-US/docs/Web/API/Node/previousSibling) استفاده کنید.

## مقدار

یک {{domxref("Node")}} که خواهر/برادر بعدی گره فعلی را نشان می‌دهد، یا اگر وجود نداشته باشد `null`.

## مثال

```html
<div id="div-1">Here is div-1</div>
<div id="div-2">Here is div-2</div>
<br />
<output><em>Not calculated.</em></output>
```

```js
let el = document.getElementById("div-1").nextSibling;
let i = 1;

let result = "Siblings of div-1:\n";

while (el) {
  result += `${i}. ${el.nodeName}\n`;
  el = el.nextSibling;
  i++;
}

const output = document.querySelector("output");
output.innerText = result;
```

{{ EmbedLiveSample("Example", "100%", 500)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.nextElementSibling")}}
- {{domxref("Node.previousSibling")}}