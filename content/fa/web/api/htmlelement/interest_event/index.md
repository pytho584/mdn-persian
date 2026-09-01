```
---
title: "HTMLElement: interest event"
slug: Web/API/HTMLElement/interest_event
page-type: web-api-event
status:
  - experimental
  - non-standard
browser-compat: api.HTMLElement.interest_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}{{non-standard_header}}

رویداد **`interest`** از رابط {{domxref("HTMLElement")}}، زمانی که علاقه به عنصر هدف یک [فراخوان علاقه (interest invoker)](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) نشان داده می‌شود، روی آن عنصر رخ می‌دهد و امکان اجرای کد را در پاسخ فراهم می‌کند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("interest", (event) => { })

oninterest = (event) => { }
```

## نوع رویداد

یک {{domxref("InterestEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("InterestEvent")}}

## مثال‌ها

### استفاده پایه از رویداد interest invoker

در این مثال، از رویدادهای `interest` و `loseinterest` استفاده می‌کنیم تا مشخص شود چه زمانی روی یک عنصر {{htmlelement("button")}} که به‌عنوان فراخوان علاقه عمل می‌کند، علاقه نشان داده می‌شود و چه زمانی از بین می‌رود. این کار را با نوشتن پیام‌هایی در محتوای متنی عنصر هدف {{htmlelement("p")}} انجام می‌دهیم.

#### HTML

رابطه بین عنصر `<button>` به‌عنوان فراخوان علاقه و عنصر هدف `<p>` را با تنظیم مقدار ویژگی `interestfor` عنصر `<button>` برای برابر بودن با `id` عنصر `<p>` برقرار می‌کنیم.

```html live-sample___basic-interest-invoker
<button href="#" interestfor="mytarget">Interest invoker</button>
<p id="mytarget">No interest being shown currently.</p>
```

#### جاوااسکریپت

یک ارجاع به عنصر `<button>` و عنصر هدفش را از طریق ویژگی {{domxref("HTMLButtonElement.interestForElement", "interestForElement")}} دریافت می‌کنیم.

```js live-sample___basic-interest-invoker
const invoker = document.querySelector("[interestfor]");
const target = invoker.interestForElement;
```

سپس دو شنونده رویداد روی عنصر هدف، یکی برای رویداد `interest` و یکی برای رویداد `loseinterest` تنظیم می‌کنیم.

- وقتی علاقه نشان داده می‌شود، محتوای متنی عنصر هدف `<p>` را به‌روزرسانی می‌کنیم تا رویداد و عنصری که آن را فعال کرده را گزارش دهد؛ در این مثال، آن عنصر `<button>` است. توجه کنید که می‌توانید از طریق ویژگی {{domxref("InterestEvent.source", "source")}} شیء رویداد، به فراخوان علاقه دسترسی پیدا کنید.
- وقتی علاقه از بین می‌رود، متن پاراگراف را به‌روزرسانی می‌کنیم تا نشان دهد دیگر علاقه‌ای نشان داده نمی‌شود.

```js live-sample___basic-interest-invoker
target.addEventListener("interest", (e) => {
  target.textContent = `Interest shown via the ${e.source.tagName} element.`;
});

target.addEventListener("loseinterest", () => {
  target.textContent = `Interest lost.`;
});
```

#### نتیجه

نمونه این‌گونه نمایش داده می‌شود:

{{embedlivesample("basic-interest-invoker", "100%", "100")}}

سعی کنید به دکمه علاقه نشان دهید و آن را از دست بدهید (مثلاً با قرار دادن نشانگر روی آن یا فوکوس کردن آن) تا ببینید متن `<p>` چگونه تغییر می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("HTMLElement.loseinterest_event", "loseinterest")}}
- [Popover API](/en-US/docs/Web/API/Popover_API)
- [استفاده از interest invokerها](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)
```