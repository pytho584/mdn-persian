---
title: "Element: currentCSSZoom property"
short-title: currentCSSZoom
slug: Web/API/Element/currentCSSZoom
page-type: web-api-instance-property
browser-compat: api.Element.currentCSSZoom
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`currentCSSZoom`** در رابط {{domxref("Element")}}، زومِ «موثر» [خاصیت CSS `zoom`](/en-US/docs/Web/CSS/Reference/Properties/zoom) یک عنصر را با در نظر گرفتن زوم اعمال‌شده روی آن عنصر و تمام عناصر والد آن ارائه می‌دهد.

این مقدار با ضرب کردن مقادیر CSS `zoom` عنصر و همهٔ والدهایش به دست می‌آید. برای مثال، اگر سه عنصر با مقادیر زوم ۲، ۱٫۵ و ۳ به‌صورت تو در تو قرار گرفته باشند، عمیق‌ترین عنصر مقدار `currentCSSZoom` برابر ۹ خواهد داشت. اگر عنصر جعبهٔ CSS نداشته باشد، مثلاً به این دلیل که `display: none` روی خود عنصر یا یکی از والدهایش تنظیم شده باشد، مقدار `currentCSSZoom` برابر ۱ قرار می‌گیرد.

توجه داشته باشید که برخی روش‌ها مانند {{domxref("Element.getBoundingClientRect()")}} ابعاد و موقعیت را نسبت به viewport برمی‌گردانند و بنابراین آثار CSS `zoom` را شامل می‌شوند. سایر ویژگی‌ها و روش‌ها مقادیری را برمی‌گردانند که نسبت به خود عنصر هستند و آثار زوم را شامل نمی‌شوند. از جملهٔ این موارد می‌توان به ویژگی‌های `client*` مانند {{domxref("Element.clientHeight")}}، روش‌های `scroll*()` مانند {{domxref("Element.scroll()")}} و ویژگی‌های `offset*` مانند {{domxref("HTMLElement.offsetHeight")}} اشاره کرد. از ویژگی `currentCSSZoom` می‌توان برای مقیاس‌بندی این مقادیر و تنظیم آثار زوم استفاده کرد.

## مقدار

عددی که زوم موثر CSS روی عنصر را نشان می‌دهد، یا ۱ اگر عنصر رندر نشده باشد.

## مثال‌ها

این مثال نشان می‌دهد که `currentCSSZoom` چگونه محاسبه می‌شود.

ابتدا ساختاری تو در تو از عناصر `<div>` تعریف می‌کنیم که در آن «parent» بدون زوم است و شامل عنصر تو در توی «child1» با اعمال `zoom: 2` است. این عنصر نیز به نوبهٔ خود شامل عنصر تو در توی «child2» با اعمال `zoom: 3` است. عنصر «child2» شامل دو عنصر تو در تو است که یکی از آن‌ها رندر نمی‌شود و هیچ‌کدام ویژگی `zoom` رویشان اعمال نشده است.

```html
<div id="parent">
  parent
  <div style="zoom: 2" id="child1">
    child1 (zoom: 2)
    <div style="zoom: 3" id="child2">
      child2 (zoom: 3)
      <div id="child3-rendered">child3-rendered</div>
      <div style="display: none" id="child3-not-rendered">
        child3-not-rendered
      </div>
    </div>
  </div>
</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 95px;
  overflow: scroll;
  margin: 10px;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

کد جاوااسکریپت مقدار زوم اعمال‌شده در هر سطح را همراه با مقدار `currentCSSZoom` آن ثبت می‌کند.

```js
if ("currentCSSZoom" in Element.prototype) {
  const parent = document.querySelector("#parent");
  log(`parent (unzoomed). currentCSSZoom: ${parent.currentCSSZoom}`);
  const child1 = document.querySelector("#child1");
  log(`child1 (zoom: 2). currentCSSZoom: ${child1.currentCSSZoom}`);
  const child2 = document.querySelector("#child2");
  log(`child2 (zoom: 2). currentCSSZoom: ${child2.currentCSSZoom}`);
  const child3Rendered = document.querySelector("#child3-rendered");
  log(
    `child3-rendered (unzoomed). currentCSSZoom: ${child3Rendered.currentCSSZoom}`,
  );
  const child3NotRendered = document.querySelector("#child3-not-rendered");
  log(
    `child3-not-rendered (not rendered): ${child3NotRendered.currentCSSZoom}`,
  );
} else {
  log("Element.currentCSSZoom not supported in this browser");
}
```

ساختار رندر شدهٔ `<div>` و لاگ حاصل در زیر نشان داده شده است. ابتدا توجه کنید که parent، child1 و child2 به ترتیب سطوح زوم ۱، ۲ و ۳ دارند و با اندازه‌های ۱، ۲ و ۶ برابر متن parent رندر می‌شوند. این موضوع در مقادیر ثبت‌شدهٔ `currentCSSZoom` بازتاب یافته است.

عنصر `<div>` با شناسهٔ `child3-rendered` ویژگی `zoom` را تنظیم‌شده ندارد، اما مقدار `currentCSSZoom` برابر ۶ را به ارث می‌برد، همان‌طور که در لاگ دیده می‌شود. عنصر `<div>` آخر رندر نمی‌شود و بنابراین مقدار `currentCSSZoom` آن برابر ۱ است.

{{EmbedLiveSample('Examples', '100%', "400px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [CSS `zoom`](/en-US/docs/Web/CSS/Reference/Properties/zoom)