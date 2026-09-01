---
title: "HTMLElement: loseinterest event"
slug: Web/API/HTMLElement/loseinterest_event
page-type: web-api-event
status:
  - experimental
  - non-standard
browser-compat: api.HTMLElement.loseinterest_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}{{non-standard_header}}

رویداد **`loseinterest`** در رابط {{domxref("HTMLElement")}} روی عنصر هدف یک [فراخوان علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) (interest invoker) صادر می‌شود وقتی علاقه از دست برود؛ این امکان را می‌دهد تا در پاسخ، کد اجرا شود.

این رویداد معمولاً [قابل لغو](/en-US/docs/Web/API/Event/cancelable) است، به‌جز زمانی که کاربر کلید <kbd>Esc</kbd> را فشار می‌دهد تا علاقه را از همه‌ی فراخوان‌های علاقه موجود در سند از دست بدهد.

## سینتکس

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا برای تنظیم یک ویژگی مدیریت رویداد (event handler property)، از سینتکس زیر استفاده کنید:

```js-nolint
addEventListener("loseinterest", (event) => { })

onloseinterest = (event) => { }
```

## نوع رویداد

یک {{domxref("InterestEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("InterestEvent")}}

## مثال‌ها

### استفاده‌ی پایه از رویداد فراخوان علاقه

در این مثال، از رویدادهای `interest` و `loseinterest` استفاده می‌کنیم تا زمانی را گزارش کنیم که به یک عنصر {{htmlelement("button")}} که به‌عنوان فراخوان علاقه عمل می‌کند، علاقه نشان داده می‌شود یا از دست می‌رود. این کار را با نوشتن پیام در محتوای متنی عنصر هدف {{htmlelement("p")}} انجام می‌دهیم.

#### HTML

رابطه‌ی بین عنصر `<button>` به‌عنوان فراخوان علاقه و عنصر هدف `<p>` را با قرار دادن مقدار ویژگی `interestfor` عنصر `<button>` برابر با `id` عنصر `<p>` برقرار می‌کنیم.

```html live-sample___basic-interest-invoker
<button href="#" interestfor="mytarget">Interest invoker</button>
<p id="mytarget">No interest being shown currently.</p>
```

#### JavaScript

ارجاعی به عنصر `<button>` و عنصر هدف آن را از طریق ویژگی {{domxref("HTMLButtonElement.interestForElement", "interestForElement")}} به دست می‌آوریم.

```js live-sample___basic-interest-invoker
const invoker = document.querySelector("[interestfor]");
const target = invoker.interestForElement;
```

سپس دو شنونده‌ی رویداد روی عنصر هدف تنظیم می‌کنیم؛ یکی برای رویداد `interest` و دیگری برای رویداد `loseinterest`.

- وقتی علاقه نشان داده می‌شود، محتوای متنی عنصر هدف `<p>` را به‌روزرسانی می‌کنیم تا رویداد و عنصر محرک آن را گزارش دهد؛ در این مثال، آن عنصر `<button>` است. توجه کنید که می‌توانید ارجاعی به فراخوان علاقه را از طریق ویژگی {{domxref("InterestEvent.source", "source")}} آبجکت رویداد به دست آورید.
- وقتی علاقه از دست می‌رود، متن پاراگراف را به‌روزرسانی می‌کنیم تا گزارش دهد که دیگر علاقه نشان داده نمی‌شود.

#### نتیجه

این مثال به این شکل نمایش داده می‌شود:

{{embedlivesample("basic-interest-invoker", "100%", "100")}}

سعی کنید به دکمه علاقه نشان دهید و آن را از دست بدهید (مثلاً با قرار دادن نشانگر روی آن یا فوکوس کردن به آن) تا ببینید متن `<p>` چگونه تغییر می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("HTMLElement.interest_event", "interest")}}
- [Popover API](/en-US/docs/Web/API/Popover_API)
- [استفاده از فراخوان‌های علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)