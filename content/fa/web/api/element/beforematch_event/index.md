---
title: "Element: beforematch event"
short-title: beforematch
slug: Web/API/Element/beforematch_event
page-type: web-api-event
browser-compat: api.Element.beforematch_event
---

{{APIRef("DOM")}}

یک عنصر زمانی رویداد **`beforematch`** را دریافت می‌کند که در حالت _hidden until found_ (پنهان تا زمان یافتن) قرار داشته باشد و مرورگر در آستانهٔ آشکار کردن محتوای آن باشد، زیرا کاربر آن محتوا را از طریق قابلیت «یافتن در صفحه» یا پیمایش به قطعه (fragment navigation) پیدا کرده است.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("beforematch", (event) => { })

onbeforematch = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نکات استفاده

ویژگی [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) در HTML مقدار `until-found` را می‌پذیرد: وقتی این مقدار مشخص شود، عنصر پنهان می‌ماند اما محتوای آن برای قابلیت «یافتن در صفحه» مرورگر یا برای پیمایش به قطعه در دسترس خواهد بود. وقتی این قابلیت‌ها باعث پیمایش به عنصری در زیردرختی با حالت _hidden until found_ شوند، مرورگر این کارها را انجام می‌دهد:

1. رویداد `beforematch` را روی آن عنصر پنهان صادر می‌کند
2. ویژگی `hidden` را از عنصر حذف می‌کند
3. به سمت عنصر پیمایش می‌کند

## مثال‌ها

### استفاده از beforematch

در این مثال، دو عنصر {{HTMLElement("div")}} داریم. اولی قابل مشاهده است و دومی ویژگی‌های `hidden="until-found"` و `id="until-found-box"` را دارد. عنصری که شناسهٔ `until-found-box` دارد دارای حاشیهٔ نقطه‌چین قرمز و پس‌زمینهٔ خاکستری است.

همچنین یک پیوند داریم که به قطعهٔ `"until-found-box"` اشاره می‌کند و جاوااسکریپتی که به رویداد `beforematch` روی همان عنصر پنهان گوش می‌دهد. کنترل‌کنندهٔ رویداد محتوای متنی جعبه را تغییر می‌دهد تا عملی را نشان دهد که می‌تواند هنگام برداشته‌شدن حالت _hidden until found_ رخ دهد.

#### HTML

```html
<a href="#until-found-box">Go to hidden content</a>

<div>I'm not hidden</div>
<div id="until-found-box" hidden="until-found">Hidden until found</div>
```

```html hidden
<button id="reset">Reset</button>
```

#### CSS

```css
div {
  height: 40px;
  width: 300px;
  border: 5px dashed black;
  margin: 1rem 0;
  padding: 1rem;
  font-size: 2rem;
}

div#until-found-box {
  color: red;
  border: 5px dotted red;
  background-color: lightgray;
}
```

#### JavaScript

```js
const untilFound = document.querySelector("#until-found-box");
untilFound.addEventListener(
  "beforematch",
  () => (untilFound.textContent = "I've been revealed!"),
);
```

```js hidden
document.querySelector("#reset").addEventListener("click", () => {
  document.location.hash = "";
  document.location.reload();
});
```

#### نتیجه

کلیک روی دکمهٔ «رفتن به محتوای پنهان» به عنصر در حالت _hidden until found_ پیمایش می‌کند. رویداد `beforematch` صادر می‌شود، محتوای متنی به‌روزرسانی می‌شود و سپس محتوای عنصر نمایش داده می‌شود (ویژگی `hidden` حذف می‌شود).

برای اجرای دوبارهٔ مثال، روی «بارگذاری مجدد» کلیک کنید.

{{EmbedLiveSample("Using beforematch", "", 300)}}

اگر مرورگر شما از مقدار شمارشی `"until-found"` برای ویژگی `hidden` پشتیبانی نکند، دومین `<div>` پنهان خواهد بود (زیرا پیش از اضافه‌شدن مقدار `until-found`، ویژگی `hidden` یک ویژگی بولی بود).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) در HTML