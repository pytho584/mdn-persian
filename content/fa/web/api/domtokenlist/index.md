---
title: DOMTokenList
slug: Web/API/DOMTokenList
page-type: web-api-interface
browser-compat: api.DOMTokenList
---

{{APIRef("DOM")}}

رابطهٔ **`DOMTokenList`** مجموعه‌ای از توکن‌های جدا شده با فاصله را نمایش می‌دهد. چنین مجموعه‌ای توسط {{domxref("Element.classList")}} یا {{domxref("HTMLLinkElement.relList")}} و بسیاری دیگر بازگردانده می‌شود.

یک `DOMTokenList` درست مانند اشیاء {{jsxref("Array")}} در جاوااسکریپت، از ایندکس `0` شماره‌گذاری می‌شود. `DOMTokenList` همیشه به بزرگی و کوچکی حروف حساس است.

## Instance properties

- {{domxref("DOMTokenList.length")}} {{ReadOnlyInline}}
  - : یک `integer` که تعداد اشیاء ذخیره‌شده در این شیء را نشان می‌دهد.
- {{domxref("DOMTokenList.value")}}
  - : یک ویژگی {{Glossary("stringifier")}} که مقدار فهرست را به‌صورت یک رشته بازمی‌گرداند.

## Instance methods

- {{domxref("DOMTokenList.item()")}}
  - : آیتم فهرست را بر اساس ایندکس آن بازمی‌گرداند؛ اگر ایندکس بزرگ‌تر یا مساوی `length` فهرست باشد، `null` بازمی‌گرداند.
- {{domxref("DOMTokenList.contains()")}}
  - : اگر فهرست حاوی توکن داده‌شده باشد، `true` و در غیر این صورت `false` بازمی‌گرداند.
- {{domxref("DOMTokenList.add()")}}
  - : توکن‌های مشخص‌شده را به فهرست اضافه می‌کند.
- {{domxref("DOMTokenList.remove()")}}
  - : توکن‌های مشخص‌شده را از فهرست حذف می‌کند.
- {{domxref("DOMTokenList.replace()")}}
  - : توکن را با توکن دیگری جایگزین می‌کند.
- {{domxref("DOMTokenList.supports()")}}
  - : اگر توکن داده‌شده در میان توکن‌های پشتیبانی‌شدهٔ ویژگی (attribute) مرتبط باشد، `true` بازمی‌گرداند.
- {{domxref("DOMTokenList.toggle()")}}
  - : اگر توکن در فهرست وجود داشته باشد آن را حذف می‌کند و اگر وجود نداشته باشد آن را به فهرست اضافه می‌کند. یک مقدار بولین بازمی‌گرداند که نشان می‌دهد پس از عملیات، آیا توکن در فهرست وجود دارد یا خیر.
- {{domxref("DOMTokenList.entries()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator", "", 1)}} بازمی‌گرداند که به شما امکان می‌دهد از میان تمام جفت‌های کلید/مقدار موجود در این شیء پیمایش کنید.
- {{domxref("DOMTokenList.forEach()")}}
  - : یک تابع callback داده‌شده را یک‌بار برای هر عنصر `DOMTokenList` اجرا می‌کند.
- {{domxref("DOMTokenList.keys()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator", "", 1)}} بازمی‌گرداند که به شما امکان می‌دهد از میان تمام کلیدهای جفت‌های کلید/مقدار موجود در این شیء پیمایش کنید.
- {{domxref("DOMTokenList.toString()")}}
  - : مقدار {{domxref("DOMTokenList.value")}} را به‌صورت یک رشته، شامل مقادیر فهرست که با فاصله جدا شده‌اند، بازمی‌گرداند.
- {{domxref("DOMTokenList.values()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator", "", 1)}} بازمی‌گرداند که به شما امکان می‌دهد از میان تمام مقادیر جفت‌های کلید/مقدار موجود در این شیء پیمایش کنید.

## Examples

در مثال سادهٔ زیر، فهرست کلاس‌های اعمال‌شده روی یک عنصر {{htmlelement("p")}} را با استفاده از {{domxref("Element.classList")}} به‌صورت یک `DOMTokenList` دریافت می‌کنیم، با استفاده از {{domxref("DOMTokenList.add()")}} یک کلاس اضافه می‌کنیم و سپس {{domxref("Node.textContent")}} عنصر `<p>` را برابر با آن `DOMTokenList` قرار می‌دهیم.

ابتدا، HTML:

```html
<p class="a b c"></p>
```

حالا جاوااسکریپت:

```js
let para = document.querySelector("p");
let classes = para.classList;
para.classList.add("d");
para.textContent = `paragraph classList is "${classes}"`;
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## Trimming of whitespace and removal of duplicates

متدهایی که `DOMTokenList` را تغییر می‌دهند (مانند {{domxref("DOMTokenList.add()")}}) به‌طور خودکار هر {{Glossary("Whitespace")}} اضافی را حذف (trim) کرده و مقادیر تکراری را از فهرست حذف می‌کنند. برای مثال:

```html
<span class="    d   d e f"></span>
```

```js
let span = document.querySelector("span");
let classes = span.classList;
span.classList.add("x");
span.textContent = `span classList is "${classes}"`;
```

خروجی به این شکل است:

{{ EmbedLiveSample('Trimming_of_whitespace_and_removal_of_duplicates', '100%', 60) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}