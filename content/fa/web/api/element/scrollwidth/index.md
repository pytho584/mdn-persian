---
title: "Element: scrollWidth property"
short-title: scrollWidth
slug: Web/API/Element/scrollWidth
page-type: web-api-instance-property
browser-compat: api.Element.scrollWidth
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`scrollWidth`** از رابط {{domxref("Element")}} اندازه‌گیری عرض محتوای یک عنصر است، از جمله محتوایی که به دلیل سرریز روی صفحه نمایش دیده نمی‌شود.

مقدار `scrollWidth` برابر است با حداقل عرضی که عنصر برای جای دادن تمام محتوا در نمایشگر (viewport) بدون نیاز به نوار پیمایش افقی لازم دارد. عرض به همان روش {{domxref("Element.clientWidth", "clientWidth")}} اندازه‌گیری می‌شود: شامل فاصلهٔ داخلی (padding) عنصر است، اما شامل مرز (border)، فاصلهٔ بیرونی (margin) یا نوار پیمایش عمودی (در صورت وجود) نمی‌شود. همچنین می‌تواند عرض شبه‌عنصرهایی مانند {{cssxref("::before")}} یا {{cssxref("::after")}} را نیز شامل شود. اگر محتوای عنصر بدون نیاز به نوار پیمایش افقی جا شود، `scrollWidth` آن برابر با {{domxref("Element.clientWidth", "clientWidth")}} خواهد بود.

## مقدار

یک عدد صحیح.

## مثال‌ها

### تشخیص محتوای سرریزشده

در این مثال، از ویژگی `scrollWidth` برای بررسی اینکه آیا محتوای یک عنصر از مرزهای آن سرریز شده است استفاده می‌کنیم. دو عنصر `div` داریم: اولی با عرض `100px` و دومی بدون عرض ثابت. محتوای آنها دقیقاً یکسان است و پیامی دربارهٔ اینکه آیا هر کدام از ظرف خود سرریز شده‌اند نمایش می‌دهیم.

#### HTML

```html
<div id="div1">FooBar-FooBar-FooBar-FooBar</div>
<button id="button1">Check for overflow</button>
<pre id="log1"></pre>
<div id="div2">FooBar-FooBar-FooBar-FooBar</div>
<button id="button2">Check for overflow</button>
<pre id="log2"></pre>
```

#### CSS

```css
div {
  padding: 0.15em;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

button {
  margin: 0.15em 0 0.5em 0;
}

pre {
  margin: 0.5em 0;
}

#div1 {
  width: 100px;
}

#log1 {
  margin-bottom: 2em;
}
```

#### JavaScript

```js
const button1 = document.getElementById("button1");
const button2 = document.getElementById("button2");

const div1 = document.getElementById("div1");
const div2 = document.getElementById("div2");

const log1 = document.getElementById("log1");
const log2 = document.getElementById("log2");

// Check if the scrollWidth is bigger than the clientWidth or not
function isOverflowing(element) {
  return element.scrollWidth > element.clientWidth;
}

function checkOverflow(element, log) {
  if (isOverflowing(element)) {
    log.innerText = `Content is overflowing, scrollWidth is ${element.scrollWidth}px`;
  } else {
    log.innerText = `No overflows, scrollWidth is ${element.scrollWidth}px`;
  }
}

button1.addEventListener("click", () => {
  checkOverflow(div1, log1);
});

button2.addEventListener("click", () => {
  checkOverflow(div2, log2);
});
```

#### نتیجه

برای بررسی اینکه آیا محتوا از ظرف‌ها سرریز شده است، روی دکمه‌ها کلیک کنید.

{{EmbedLiveSample("detecting_overflowing_content", "100%", "190")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Determining the dimensions of elements](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetWidth")}}
- {{domxref("Element.clientWidth")}}
- {{domxref("Element.scrollHeight")}}
- {{domxref("Element.scrollLeft")}}
- {{domxref("Element.scrollTop")}}
- {{domxref("Element.getBoundingClientRect()")}}
- {{domxref("Element.scrollTo()")}}