---
title: "Element: getBoundingClientRect() method"
short-title: getBoundingClientRect()
slug: Web/API/Element/getBoundingClientRect
page-type: web-api-instance-method
browser-compat: api.Element.getBoundingClientRect
---

{{APIRef("DOM")}}

متد **`Element.getBoundingClientRect()`** یک شیء {{domxref("DOMRect")}} برمی‌گرداند که اطلاعاتی درباره اندازه یک عنصر و موقعیت آن نسبت به [viewport](/en-US/docs/Glossary/Viewport) فراهم می‌کند.

## نحو (Syntax)

```js-nolint
getBoundingClientRect()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

مقدار بازگشتی یک شیء {{domxref("DOMRect")}} است که کوچکترین مستطیل شامل کل عنصر، شامل padding و border-width آن را نشان می‌دهد. خصوصیات `left`، `top`، `right`، `bottom`، `x`، `y`، `width` و `height` موقعیت و اندازه مستطیل کلی را بر حسب پیکسل توصیف می‌کنند. خصوصیات غیر از `width` و `height` نسبت به گوشه بالا-چپ viewport هستند.

![شیء DOMRect که کوچکترین مستطیل حاوی کل عنصر است](element-box-diagram.png)

خصوصیات `width` و `height` شیء {{domxref("DOMRect")}} بازگشتی از این متد، شامل `padding` و `border-width` می‌شوند، نه فقط عرض/ارتفاع محتوا. در مدل جعبه استاندارد، این مقدار برابر با `width` یا `height` عنصر + `padding` + `border-width` خواهد بود. اما اگر [`box-sizing: border-box`](/en-US/docs/Web/CSS/Reference/Properties/box-sizing) برای عنصر تنظیم شده باشد، این مقدار مستقیماً برابر با `width` یا `height` آن خواهد بود.

می‌توان مقدار بازگشتی را به عنوان اتحاد مستطیل‌های بازگشتی از {{domxref("Element.getClientRects", "getClientRects()")}} برای آن عنصر در نظر گرفت، یعنی جعبه‌های مرزی CSS مرتبط با عنصر.

جعبه‌های مرزی خالی کاملاً نادیده گرفته می‌شوند. اگر تمام جعبه‌های مرزی عنصر خالی باشند، مستطیلی با `width` و `height` صفر بازگردانده می‌شود که در آن `top` و `left` برابر با گوشه بالا-چپ جعبه مرزی برای اولین جعبه CSS (به ترتیب محتوا) برای عنصر است.

میزان پیمایش انجام‌شده در ناحیه viewport (یا هر عنصر قابل پیمایش دیگری) هنگام محاسبه مستطیل مرزی در نظر گرفته می‌شود. این بدان معناست که لبه‌های مرزی مستطیل (`top`، `right`، `bottom`، `left`) هر بار که موقعیت پیمایش تغییر می‌کند، مقادیرشان تغییر می‌کند (زیرا مقادیر آنها نسبت به viewport است و مطلق نیستند).

اگر به مستطیل مرزی نسبت به گوشه بالا-چپ سند نیاز دارید، کافی است موقعیت پیمایش فعلی را به خصوصیات `top` و `left` اضافه کنید (این مقادیر را می‌توان با استفاده از {{domxref("window.scrollY")}} و {{domxref("window.scrollX")}} به دست آورد) تا مستطیل مرزی مستقل از موقعیت پیمایش فعلی به دست آید.

## مثال‌ها

### مثال پایه

این مثال ساده شیء `DOMRect` مربوط به مستطیل مرزی viewport یک عنصر `<div>` ساده را بازیابی کرده و خصوصیات آن را در زیر آن چاپ می‌کند.

```html
<div></div>
```

```css
div {
  width: 400px;
  height: 200px;
  padding: 20px;
  margin: 50px auto;
  background: purple;
}
```

```js
let elem = document.querySelector("div");
let rect = elem.getBoundingClientRect();
for (const key in rect) {
  if (typeof rect[key] !== "function") {
    let para = document.createElement("p");
    para.textContent = `${key} : ${rect[key]}`;
    document.body.appendChild(para);
  }
}
```

{{EmbedLiveSample('Basic', '100%', 640)}}

توجه کنید که `width`/`height` برابر با `width`/`height` عنصر + `padding` آن است.

همچنین توجه کنید که مقادیر `x`/`left`، `y`/`top`، `right` و `bottom` برابر با فاصله مطلق از لبه مربوطه viewport تا آن سمت عنصر هستند.

### پیمایش

این مثال نشان می‌دهد که وقتی سند پیمایش می‌شود، مستطیل مرزی viewport چگونه تغییر می‌کند.

```html
<div id="example"></div>
<div id="controls"></div>
```

```css
div#example {
  width: 400px;
  height: 200px;
  padding: 20px;
  margin: 50px auto;
  background: purple;
}

body {
  padding-bottom: 1000px;
}
p {
  margin: 0;
}
```

```js
function update() {
  const container = document.getElementById("controls");
  const elem = document.getElementById("example");
  const rect = elem.getBoundingClientRect();

  container.textContent = "";
  for (const key in rect) {
    if (typeof rect[key] !== "function") {
      let para = document.createElement("p");
      para.textContent = `${key} : ${rect[key]}`;
      container.appendChild(para);
    }
  }
}

document.addEventListener("scroll", update);
update();
```

{{EmbedLiveSample('Scrolling', '100%', 640)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.getClientRects", "getClientRects()")}}