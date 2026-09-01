---
title: "HTMLElement: innerText property"
---

---
title: "HTMLElement: innerText property"
short-title: innerText
slug: Web/API/HTMLElement/innerText
page-type: web-api-instance-property
browser-compat: api.HTMLElement.innerText
---

{{APIRef("HTML DOM")}}

ویژگی **`innerText`** در رابط {{domxref("HTMLElement")}} محتوای متنی رندر شدهٔ یک گره و نوادگان آن را نمایش می‌دهد.

به‌عنوان getter، این ویژگی متنی را تقریب می‌زند که کاربر اگر محتوای عنصر را با مکان‌نما انتخاب و سپس در کلیپ‌بورد کپی کند، دریافت می‌کند. به‌عنوان setter، این ویژگی فرزندان عنصر را با مقدار داده‌شده جایگزین می‌کند و هر گونه شکست خط را به عنصر {{HTMLElement("br")}} تبدیل می‌کند.

> [!NOTE]
> `innerText` به‌راحتی با {{domxref("Node.textContent")}} اشتباه گرفته می‌شود، اما تفاوت‌های مهمی بین این دو وجود دارد. در اصل، `innerText` از ظاهر رندر شدهٔ متن آگاه است، در حالی که `textContent` چنین نیست.

## مقدار

یک رشته (string) که محتوای متنی رندر شدهٔ یک عنصر را نشان می‌دهد.

اگر خود عنصر [رندر نمی‌شود](https://html.spec.whatwg.org/multipage/rendering.html#being-rendered) (مثلاً از سند جدا شده باشد یا از دید پنهان باشد)، مقدار بازگشتی همان ویژگی {{domxref("Node.textContent")}} خواهد بود.

> [!WARNING]
> تنظیم `innerText` روی یک گره، _همه_ فرزندان گره را حذف می‌کند و آن‌ها را با یک گره متنی واحد حاوی مقدار رشتهٔ داده‌شده جایگزین می‌کند.

## مثال‌ها

این مثال `innerText` را با {{domxref("Node.textContent")}} مقایسه می‌کند. توجه کنید که `innerText` چگونه از چیزهایی مانند عناصر {{htmlElement("br")}} آگاه است و عناصر پنهان را نادیده می‌گیرد.

### HTML

```html
<h3>Source element:</h3>
<p id="source">
  <style>
    #source {
      color: red;
    }
    #text {
      text-transform: uppercase;
    }
  </style>
  <span id="text">
    Take a look at<br />
    how this text<br />
    is interpreted below.
  </span>
  <span style="display:none">HIDDEN TEXT</span>
</p>
<h3>Result of textContent:</h3>
<textarea id="textContentOutput" rows="18" cols="40" readonly>…</textarea>
<h3>Result of innerText:</h3>
<textarea id="innerTextOutput" rows="6" cols="40" readonly>…</textarea>
```

### JavaScript

```js
const source = document.getElementById("source");
const textContentOutput = document.getElementById("textContentOutput");
const innerTextOutput = document.getElementById("innerTextOutput");

textContentOutput.value = source.textContent;
innerTextOutput.value = source.innerText;
```

### نتیجه

{{EmbedLiveSample("Examples", 700, 650)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement.innerText")}}
- {{domxref("HTMLElement.outerText")}}
- {{domxref("Element.innerHTML")}}