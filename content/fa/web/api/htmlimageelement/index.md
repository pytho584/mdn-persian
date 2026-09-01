---
title: HTMLImageElement
slug: Web/API/HTMLImageElement
page-type: web-api-interface
browser-compat: api.HTMLImageElement
---

{{APIRef("HTML DOM")}}

رابط کاربری **`HTMLImageElement`** یک عنصر HTML {{HTMLElement("img")}} را نمایش می‌دهد و ویژگی‌ها و روش‌های مورد استفاده برای دستکاری عناصر تصویر را فراهم می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("HTMLImageElement.Image()", "Image()")}}
  - : سازنده `Image()` یک شیء `HTMLImageElement` جدید ایجاد و بازمی‌گرداند که یک عنصر HTML {{HTMLElement("img")}} را نشان می‌دهد که به هیچ درخت DOM متصل نیست. این سازنده پارامترهای اختیاری عرض و ارتفاع را می‌پذیرد. هنگامی که بدون پارامتر فراخوانی شود، `new Image()` معادل فراخوانی {{DOMxRef("Document.createElement()", "document.createElement('img')")}} است.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLImageElement.alt")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`alt`](/en-US/docs/Web/HTML/Reference/Elements/img#alt) است و بنابراین محتوای جایگزین بازگشتی را نشان می‌دهد که در صورت بارگذاری نشدن تصویر نمایش داده می‌شود.
- {{domxref("HTMLImageElement.attributionSrc")}} {{securecontext_inline}} {{deprecated_inline}} {{non-standard_inline}}
  - : ویژگی [`attributionsrc`](/en-US/docs/Web/HTML/Reference/Elements/img#attributionsrc) را در یک عنصر {{htmlelement("img")}} به صورت برنامه‌نویسی تنظیم و دریافت می‌کند و مقدار آن ویژگی را منعکس می‌کند. `attributionsrc` مشخص می‌کند که می‌خواهید مرورگر یک هدر {{httpheader("Attribution-Reporting-Eligible")}} را همراه با درخواست تصویر ارسال کند. در سمت سرور، این برای راه‌اندازی ارسال هدر {{httpheader("Attribution-Reporting-Register-Source")}} یا {{httpheader("Attribution-Reporting-Register-Trigger")}} در پاسخ، به ترتیب برای ثبت یک [منبع انتساب مبتنی بر تصویر](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#html-based_event_sources) یا [محرک انتساب مبتنی بر تصویر](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers#html-based_attribution_triggers) استفاده می‌شود.
- {{domxref("HTMLImageElement.complete")}} {{ReadOnlyInline}}
  - : یک مقدار بولی بازمی‌گرداند که اگر مرورگر واکشی تصویر را به پایان رسانده باشد، چه موفقیت‌آمیز باشد چه نه، `true` است. این بدان معناست که این مقدار همچنین اگر تصویر هیچ مقدار {{domxref("HTMLImageElement.src", "src")}} برای بارگذاری نداشته باشد، `true` است.
- {{domxref("HTMLImageElement.crossOrigin")}}
  - : یک رشته که تنظیمات CORS را برای این عنصر تصویر مشخص می‌کند. برای جزئیات بیشتر به [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید. در صورت عدم استفاده از CORS ممکن است `null` باشد.
- {{domxref("HTMLImageElement.currentSrc")}} {{ReadOnlyInline}}
  - : یک رشته بازمی‌گرداند که نشانی اینترنتی را نشان می‌دهد که تصویر نمایش داده شده در حال حاضر از آن بارگذاری شده است. این ممکن است با تغییر شرایط، طبق هر [پرسش رسانه‌ای](/en-US/docs/Web/CSS/Guides/Media_queries) که در جای خود قرار دارد، تغییر کند.
- {{domxref("HTMLImageElement.decoding")}}
  - : یک رشته اختیاری که نشان‌دهنده راهنمایی به مرورگر در مورد نحوه رمزگشایی تصویر است. اگر این مقدار ارائه شود، باید یکی از مقادیر مجاز ممکن باشد: `sync` برای رمزگشایی همزمان تصویر، `async` برای رمزگشایی ناهمزمان، یا `auto` برای عدم ترجیح (که پیش‌فرض است). برای جزئیات در مورد پیامدهای مقادیر این ویژگی، صفحه {{domxref("HTMLImageElement.decoding", "decoding")}} را مطالعه کنید.
- {{domxref("HTMLImageElement.fetchPriority")}}
  - : یک رشته اختیاری که نشان‌دهنده راهنمایی به مرورگر در مورد اولویت واکشی تصویر نسبت به سایر تصاویر است. اگر این مقدار ارائه شود، باید یکی از مقادیر مجاز ممکن باشد: `high` برای واکشی با اولویت بالا، `low` برای واکشی با اولویت پایین، یا `auto` برای عدم ترجیح (که پیش‌فرض است).
- {{domxref("HTMLImageElement.height")}}
  - : یک مقدار صحیح که ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/img#height) را منعکس می‌کند و ارتفاع رندر شده تصویر را بر حسب پیکسل CSS نشان می‌دهد.
- {{domxref("HTMLImageElement.isMap")}}
  - : یک مقدار بولی که ویژگی HTML [`ismap`](/en-US/docs/Web/HTML/Reference/Elements/img#ismap) را منعکس می‌کند و نشان می‌دهد که تصویر بخشی از یک نقشه تصویر سمت سرور است. این با نقشه تصویر سمت کاربر متفاوت است که با استفاده از یک عنصر `<img>` و یک عنصر {{HTMLElement("map")}} متناظر که شامل عناصر {{HTMLElement("area")}} برای نشان دادن مناطق قابل کلیک در تصویر است، مشخص می‌شود. تصویر _باید_ درون یک عنصر {{HTMLElement("a")}} قرار گیرد؛ برای جزئیات به صفحه `ismap` مراجعه کنید.
- {{domxref("HTMLImageElement.loading")}}
  - : یک رشته که نشان می‌دهد مرورگر باید تصویر را بلافاصله (`eager`) یا در صورت نیاز (`lazy`) بارگذاری کند.
- {{domxref("HTMLImageElement.naturalHeight")}} {{ReadOnlyInline}}
  - : یک مقدار صحیح بازمی‌گرداند که ارتفاع ذاتی تصویر را بر حسب پیکسل CSS نشان می‌دهد، در صورت وجود؛ در غیر این صورت `0` را نشان می‌دهد. این ارتفاعی است که تصویر در صورت رندر شدن با اندازه کامل طبیعی خود خواهد داشت.
- {{domxref("HTMLImageElement.naturalWidth")}} {{ReadOnlyInline}}
  - : یک مقدار صحیح که عرض ذاتی تصویر را بر حسب پیکسل CSS نشان می‌دهد، در صورت وجود؛ در غیر این صورت `0` را نشان می‌دهد. این عرضی است که تصویر در صورت رندر شدن با اندازه کامل طبیعی خود خواهد داشت.
- {{domxref("HTMLImageElement.referrerPolicy")}}
  - : یک رشته که ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/img#referrerpolicy) را منعکس می‌کند و به {{Glossary("user agent")}} می‌گوید که چگونه تصمیم بگیرد از کدام ارجاع‌دهنده برای واکشی تصویر استفاده کند. برای جزئیات در مورد مقادیر ممکن این رشته، این مقاله را مطالعه کنید.
- {{domxref("HTMLImageElement.sizes")}}
  - : یک رشته که ویژگی HTML [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) را منعکس می‌کند. این رشته فهرستی از اندازه‌های شرطی جدا شده با کاما برای تصویر را مشخص می‌کند؛ یعنی برای یک اندازه viewport معین، از اندازه تصویر خاصی استفاده شود. برای جزئیات در مورد قالب این رشته، مستندات صفحه {{domxref("HTMLImageElement.sizes", "sizes")}} را مطالعه کنید.
- {{domxref("HTMLImageElement.src")}}
  - : یک رشته که ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) را منعکس می‌کند و شامل نشانی کامل اینترنتی تصویر به همراه URI پایه است. می‌توانید با تغییر نشانی در ویژگی `src` یک تصویر متفاوت را در عنصر بارگذاری کنید.
- {{domxref("HTMLImageElement.srcset")}}
  - : یک رشته که ویژگی HTML [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) را منعکس می‌کند. این فهرستی از تصاویر کاندید را مشخص می‌کند که با کاما (',', U+002C COMMA) از هم جدا شده‌اند. هر تصویر کاندید یک نشانی اینترنتی است که به دنبال آن یک فاصله و سپس یک رشته با فرمت خاص که اندازه تصویر را نشان می‌دهد. اندازه ممکن است به صورت عرض یا مضرب اندازه مشخص شود. برای جزئیات در مورد قالب زیررشته اندازه، صفحه {{domxref("HTMLImageElement.srcset", "srcset")}} را مطالعه کنید.
- {{domxref("HTMLImageElement.useMap")}}
  - : یک رشته که ویژگی HTML [`usemap`](/en-US/docs/Web/HTML/Reference/Elements/img#usemap) را منعکس می‌کند و شامل نشانی اینترنتی محلی صفحه عنصر {{HTMLElement("map")}} است که نقشه تصویر مورد استفاده را توصیف می‌کند. نشانی محلی صفحه یک نماد پوند (هش) (`#`) به دنبال `name` عنصر `<map>` است، مانند `#my-map-element`. عنصر `<map>` به نوبه خود شامل عناصر {{HTMLElement("area")}} است که مناطق قابل کلیک در تصویر را نشان می‌دهند.
- {{domxref("HTMLImageElement.width")}}
  - : یک مقدار صحیح که ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/img#width) را منعکس می‌کند و عرض رندر شده تصویر را بر حسب پیکسل CSS نشان می‌دهد.
- {{domxref("HTMLImageElement.x")}} {{ReadOnlyInline}}
  - : یک عدد صحیح که افست افقی لبه مرز چپ جعبه طرح‌بندی CSS تصویر را نسبت مبدأ بلوک حاوی عنصر {{HTMLElement("html")}} نشان می‌دهد.
- {{domxref("HTMLImageElement.y")}} {{ReadOnlyInline}}
  - : عدد صحیح افست عمودی لبه مرز بالای جعبه طرح‌بندی CSS تصویر را نسبت مبدأ بلوک حاوی عنصر {{HTMLElement("html")}} نشان می‌دهد.

## ویژگی‌های منسوخ

- {{domxref("HTMLImageElement.align")}} {{deprecated_inline}}
  - : یک رشته که تراز تصویر را نسبت به زمینه اطراف نشان می‌دهد. مقادیر ممکن عبارتند از `"left"`, `"right"`, `"justify"` و `"center"`. این ویژگی منسوخ شده است؛ باید به جای آن از CSS (مانند {{cssxref("text-align")}} که با وجود نامش با تصاویر کار می‌کند) برای مشخص کردن تراز استفاده کنید.
- {{domxref("HTMLImageElement.border")}} {{deprecated_inline}}
  - : یک رشته که عرض حاشیه اطراف تصویر را تعریف می‌کند. این ویژگی منسوخ شده است؛ به جای آن از ویژگی CSS {{cssxref("border")}} استفاده کنید.
- {{domxref("HTMLImageElement.hspace")}} {{deprecated_inline}}
  - : یک مقدار صحیح که میزان فضای خالی (بر حسب پیکسل) را در سمت چپ و راست تصویر مشخص می‌کند.
- {{domxref("HTMLImageElement.longDesc")}} {{deprecated_inline}}
  - : یک رشته که نشانی اینترنتی را مشخص می‌کند که در آن توضیحات طولانی از محتوای تصویر یافت می‌شود. این برای تبدیل خودکار تصویر به یک پیوند ابری استفاده می‌شود. HTML مدرن باید به جای آن یک `<img>` را درون یک عنصر {{HTMLElement("a")}} که پیوند ابری را تعریف می‌کند قرار دهد.
- {{domxref("HTMLImageElement.name")}} {{deprecated_inline}}
  - : یک رشته که نام عنصر را نشان می‌دهد.
- {{domxref("HTMLImageElement.vspace")}} {{deprecated_inline}}
  - : یک مقدار صحیح که میزان فضای خالی (بر حسب پیکسل) را در بالا و پایین تصویر مشخص می‌کند.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLImageElement.decode()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که وقتی تصویر رمزگشایی شد و اضافه کردن تصویر به DOM ایمن است، حل می‌شود. این کار از توقف رندر فریم بعدی برای رمزگشایی تصویر جلوگیری می‌کند، همانطور که اگر یک تصویر رمزگشایی نشده به DOM اضافه شود، اتفاق می‌افتد.

## خطاها

اگر در حین بارگذاری یا رندر تصویر خطایی رخ دهد و یک کنترل‌کننده رویداد `onerror` برای مدیریت رویداد {{domxref("HTMLElement/error_event", "error")}} پیکربندی شده باشد، آن کنترل‌کننده رویداد فراخوانی خواهد شد. این می‌تواند در تعدادی از موقعیت‌ها رخ دهد، از جمله:

- ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) خالی یا `null` باشد.
- نشانی اینترنتی `src` مشخص شده با نشانی صفحه‌ای که کاربر در حال حاضر در آن است یکسان باشد.
- تصویر مشخص شده به نحوی خراب باشد که از بارگذاری آن جلوگیری کند.
- ابرداده تصویر مشخص شده به گونه‌ای خراب باشد که بازیابی ابعاد آن غیرممکن باشد و هیچ ابعادی در ویژگی‌های عنصر `<img>` مشخص نشده باشد.
- تصویر مشخص شده در قالبی باشد که توسط {{Glossary("user agent")}} پشتیبانی نمی‌شود.

## مثال‌ها

### ایجاد و درج یک عنصر تصویر

```js
const img1 = new Image(); // سازنده Image
img1.src = "image1.png";
img1.alt = "alt";
document.body.appendChild(img1);

const img2 = document.createElement("img"); // استفاده از DOM HTMLImageElement
img2.src = "image2.jpg";
img2.alt = "alt text";
document.body.appendChild(img2);

// استفاده از اولین تصویر در سند
alert(document.images[0].src);
```

### دریافت عرض و ارتفاع

مثال زیر استفاده از ویژگی‌های `height` و `width` را همراه با تصاویر با ابعاد مختلف نشان می‌دهد:

```html
<p>
  تصویر 1: بدون ارتفاع، عرض یا سبک
  <img id="image1" src="https://www.mozilla.org/images/mozilla-banner.gif" />
</p>

<p>
  تصویر 2: height="50", width="500", اما بدون سبک
  <img
    id="image2"
    src="https://www.mozilla.org/images/mozilla-banner.gif"
    height="50"
    width="500" />
</p>

<p>
  تصویر 3: بدون ارتفاع، عرض، اما style="height: 50px; width: 500px;"
  <img
    id="image3"
    src="https://www.mozilla.org/images/mozilla-banner.gif"
    style="height: 50px; width: 500px;" />
</p>

<div id="output"></div>
```

```js
const arrImages = [
  document.getElementById("image1"),
  document.getElementById("image2"),
  document.getElementById("image3"),
];

const objOutput = document.getElementById("output");
let strHtml = "<ul>";

for (let i = 0; i < arrImages.length; i++) {
  const img = arrImages[i];
  strHtml += `<li>image${i + 1}: height=${img.height}, width=${img.width}, style.height=${img.style.height}, style.width=${img.style.width}</li>`;
}

strHtml += "</ul>";

objOutput.innerHTML = strHtml;
```

{{EmbedLiveSample("getting width and height", "", "300")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("img")}}