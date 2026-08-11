---
title: "AbstractRange"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange"
translated_by: "n8n + AI"
---

# AbstractRange

رابط `AbstractRange` یک رابط انتزاعی است که به عنوان کلاس پایه برای تمام انواع بازه (range) در {{Glossary("DOM")}} تعریف شده است. یک **range** شیئی است که نقاط شروع و پایان یک بخش از محتوای داخل سند را مشخص می‌کند.

> [!NOTE]
> از آنجا که این رابط یک رابط انتزاعی است، شما مستقیماً شیئی از نوع `AbstractRange` نمی‌سازید. در عوض از رابط‌های [Range](https://developer.mozilla.org/en-US/docs/Web/API/Range) یا [StaticRange](https://developer.mozilla.org/en-US/docs/Web/API/StaticRange) استفاده خواهید کرد. برای درک تفاوت این دو رابط و انتخاب مورد مناسب، مستندات هر کدام را مطالعه کنید.

## ویژگی‌های نمونه (Instance properties)

- [`collapsed`](https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/collapsed) (فقط خواندنی)
  - : یک مقدار `Boolean` که اگر range **جمع‌شده** (collapsed) باشد `true` است. range جمع‌شده محدوده‌ای است که موقعیت شروع و پایان آن یکی باشد، در نتیجه طول آن صفر کاراکتر است.
- [`endContainer`](https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/endContainer) (فقط خواندنی)
  - : شیء [Node](https://developer.mozilla.org/en-US/docs/Web/API/Node) که انتهای range (مشخص‌شده با ویژگی `endOffset`) درون آن قرار دارد.
- [`endOffset`](https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/endOffset) (فقط خواندنی)
  - : یک عدد صحیح که offset (بر حسب کاراکتر) از ابتدای محتوای گره تا آخرین کاراکتری که توسط range پوشش داده می‌شود را نشان می‌دهد. این مقدار باید کمتر از طول گره `endContainer` باشد.
- [`startContainer`](https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/startContainer) (فقط خواندنی)
  - : شیء [Node](https://developer.mozilla.org/en-US/docs/Web/API/Node) در DOM که ابتدای range (مشخص‌شده با ویژگی `startOffset`) درون آن قرار دارد.
- [`startOffset`](https://developer.mozilla.org/en-US/docs/Web/API/AbstractRange/startOffset) (فقط خواندنی)
  - : یک عدد صحیح که offset (بر حسب کاراکتر) از ابتدای محتوای گره تا اولین کاراکتری که توسط range پوشش داده می‌شود را نشان می‌دهد. این مقدار باید کمتر از طول گره مشخص‌شده در `startContainer` باشد.

## متدهای نمونه (Instance methods)

_رابط `AbstractRange` هیچ متدی ارائه نمی‌کند._

## نکات استفاده

### انواع Range

تمام محدوده‌های محتوا در داخل یک [document](https://developer.mozilla.org/en-US/docs/Web/API/Document) با استفاده از نمونه‌هایی از رابط‌های مبتنی بر `AbstractRange` توصیف می‌شوند. دو رابط از این نوع وجود دارد:

- [Range](https://developer.mozilla.org/en-US/docs/Web/API/Range)
  - : رابط `Range` مدت‌هاست که وجود دارد و اخیراً بر اساس `AbstractRange` بازتعریف شده تا سایر اشکال داده‌های range نیز تعریف شوند. `Range` متدهایی ارائه می‌دهد که به شما امکان می‌دهند نقاط انتهایی range را تغییر دهید، همچنین متدهایی برای مقایسه rangeها، تشخیص اشتراک بین rangeها و موارد دیگر.
- [StaticRange](https://developer.mozilla.org/en-US/docs/Web/API/StaticRange)
  - : یک `StaticRange` یک range پایه است که پس از ایجاد نمی‌توان آن را تغییر داد. به‌طور خاص، با تغییر و جهش درخت گره‌ها، range بدون تغییر می‌ماند. این موضوع زمانی مفید است که نیاز به تعیین rangeای دارید که فقط یک‌بار استفاده می‌شود، چرا که از تأثیر عملکردی و مصرف منابع رابط پیچیده‌تر [Range](https://developer.mozilla.org/en-US/docs/Web/API/Range) جلوگیری می‌کند.

### محتوای عناصر

هنگام تلاش برای دسترسی به محتوای یک عنصر، به خاطر داشته باشید که خود عنصر یک گره است، اما هر متنی که داخل آن باشد نیز یک گره جداگانه است. برای تنظیم نقطه انتهایی range درون متن یک عنصر، ابتدا باید گره متنی داخل آن عنصر را پیدا کنید:

```js
const startElem = document.querySelector("p");
const endElem = startElem.querySelector("span");
const range = document.createRange();

range.setStart(startElem, 0);
range.setEnd(endElem, endElem.childNodes[0].length / 2);
const contents = range.cloneContents();

document.body.appendChild(contents);
```

این مثال یک range جدید به نام `range` ایجاد می‌کند و نقطه شروع آن را روی سومین گره فرزند اولین عنصر قرار می‌دهد. نقطه پایان نیز در وسط اولین فرزند span تنظیم می‌شود، سپس با استفاده از range محتوای محدوده کپی می‌شود.

برای تعیین یک محدوده از کاراکترها در یک سند، به‌طوری‌که بتواند از مرز صفر یا چند node عبور کند و تا حد ممکن در برابر تغییرات DOM مقاوم باشد، نمی‌توان offset اولین و آخرین کاراکتر را در سورس HTML مشخص کرد. چند دلیل خوب برای این موضوع وجود دارد.

اول، پس از بارگذاری صفحه، مرورگر دیگر به HTML فکر نمی‌کند. وقتی صفحه بارگذاری شد، به درختی از اشیاء DOM {{domxref("Node")}} تبدیل می‌شود؛ بنابراین باید محل شروع و پایان یک محدوده را بر اساس nodeها و موقعیت‌های درون آن‌ها تعیین کنید.

دوم، برای پشتیبانی هرچه بهتر از تغییرپذیری درخت DOM، به روشی نیاز دارید که موقعیت‌ها را نسبت به nodeهای درخت بیان کند، نه موقعیت‌های سراسری در کل سند. با تعریف نقاطی از سند به‌صورت offset درون یک node مشخص، این موقعیت‌ها حتی با افزودن، حذف یا جابه‌جایی nodeها در درخت DOM تا حد معقولی با محتوا سازگار می‌مانند. محدودیت‌های نسبتاً واضحی وجود دارد (مثلاً اگر یک node به بعد از نقطهٔ پایانی محدوده منتقل شود، یا اگر محتوای یک node به شدت تغییر کند)، اما از هیچی بهتر است.

سوم، استفاده از موقعیت‌های نسبی به node برای تعریف نقطهٔ شروع و پایان معمولاً کارایی بهتری دارد. به‌جای اینکه مرورگر (user agent) مجبور باشد کل DOM را جستجو کند تا بفهمد offset سراسری به چه چیزی اشاره دارد، می‌تواند مستقیماً به node مشخص‌شده در نقطهٔ شروع برود و از آنجا شروع کند و به‌تدریج جلو برود تا به offset داده‌شده در node پایانی برسد.

برای روشن‌تر شدن موضوع، HTML زیر را در نظر بگیرید:

```html
<div class="container">
  <div class="header">
    <img src="..." alt="" class="sitelogo" />
    <h1>The Ultimate Website</h1>
  </div>
  <article>
    <section class="entry" id="entry1">
      <h2>Section 1: An interesting thing…</h2>
      <p>A <em>very</em> interesting thing happened on the way to the forum…</p>
      <aside class="callout">
        <h2>Aside</h2>
        <p>An interesting aside to share with you…</p>
      </aside>
    </section>
  </article>
  <pre id="log"></pre>
</div>
```

پس از بارگذاری HTML و ساخته شدن نمایش DOM سند، درخت DOM حاصل به این شکل خواهد بود:

![نمودار DOM برای یک صفحهٔ وب ساده](simpledom.svg)

در این نمودار، nodeهایی که عناصر HTML را نمایش می‌دهند با رنگ سبز نشان داده شده‌اند. هر ردیف زیر آن‌ها، لایهٔ بعدی عمق درخت DOM را نشان می‌دهد. nodeهای آبی، text node هستند و متنی را که روی صفحه دیده می‌شود در خود دارند. محتوای هر عنصر در زیر آن در درخت قرار می‌گیرد و با توجه به اینکه عناصر می‌توانند شامل عناصر دیگر و text nodeها باشند، شاخه‌هایی در زیر آن‌ها ایجاد می‌شود.

اگر بخواهید محدوده‌ای بسازید که محتوای عنصر `<p>` با متن `"A <em>very</em> interesting thing happened on the way to the forum…"` را در بر بگیرد، می‌توانید این‌کار را به این صورت انجام دهید:

```js
const pRange = document.createRange();
pRange.selectNodeContents(document.querySelector("#entry1 p"));
```

از آنجا که می‌خواهیم کل محتوای عنصر `<p>` به همراه نوادگانش انتخاب شود، این روش عالی کار می‌کند.

اگر به‌جای آن بخواهیم متن "An interesting thing…" را از عنوان `<section>` (یک عنصر `<h2>`) تا پایان حروف "ve" درون عنصر `<em>` داخل پاراگراف پایین آن کپی کنیم، کد زیر این کار را انجام می‌دهد:

```js
const range = document.createRange();
const startNode = document.querySelector("section h2").childNodes[0];
range.setStart(startNode, 11);

const endNode = document.querySelector("#entry1 p em").childNodes[0];
range.setEnd(endNode, 2);

const fragment = range.cloneContents();
```

اینجا یک مسئلهٔ جالب پیش می‌آید—ما در حال گرفتن محتوا از چند node در سطوح مختلف سلسله‌مراتب DOM هستیم و همچنین فقط بخشی از یکی از آن‌ها را برمی‌داریم. نتیجه باید چه شکلی باشد؟

همان‌طور که مشخص شده، خوشبختانه مشخصات DOM دقیقاً همین مسئله را پوشش می‌دهد. به‌عنوان مثال، در اینجا ما `cloneContents()` را روی range فراخوانی می‌کنیم تا یک شیء جدید `DocumentFragment` ایجاد کند که یک زیردرخت DOM ارائه می‌کند که محتوای محدوده مشخص‌شده را تکثیر می‌کند. برای انجام این کار، `cloneContents()` تمام گره‌های لازم برای حفظ ساختار محدوده مشخص‌شده را می‌سازد، اما نه بیش از حد نیاز.

در این مثال، شروع محدوده مشخص‌شده درون گره text node زیر عنوان بخش قرار دارد، به این معنی که `DocumentFragment` جدید باید شامل یک `<h2>` و یک text node زیر آن باشد.

پایان محدوده در زیر المان `<p>` قرار دارد، بنابراین در قطعه جدید به آن نیاز خواهد بود. همچنین text node حاوی کلمه "A" نیز لازم است، چون در محدوده گنجانده شده است. در نهایت، یک `<em>` و یک text node زیر آن نیز در زیر `<p>` اضافه خواهند شد.

محتوای text nodeها سپس با آفست‌هایی که هنگام فراخوانی `setStart()` و `setEnd()` در آن text nodeها داده می‌شود تعیین می‌شود. با توجه به آفست 11 در متن heading، آن گره شامل "An interesting thing…" خواهد بود. به همین ترتیب، آخرین text node شامل "ve" خواهد بود، با توجه به درخواست دو کاراکتر اول گره پایانی.

قطعه سند حاصل به این شکل است:

![یک DocumentFragment که محتوای کلون‌شده را نشان می‌دهد](dom-fragment.svg)

به‌ویژه توجه کنید که محتوای این قطعه همگی _پایین‌تر_ از والد مشترک بالاترین گره‌های داخل آن است. والد `<section>` برای تکثیر محتوای کلون‌شده لازم نیست، بنابراین گنجانده نشده است.

## Example

این قطعه ساده HTML را در نظر بگیرید.

```html
<p><strong>This</strong> is a paragraph.</p>
```

تصور کنید با استفاده از یک `Range` کلمه "paragraph" را از این استخراج کنیم. کد انجام این کار به شکل زیر است:

```js
const paraNode = document.querySelector("p");
const paraTextNode = paraNode.childNodes[1];

const range = document.createRange();
range.setStart(paraTextNode, 6);
range.setEnd(paraTextNode, paraTextNode.length - 1);

const fragment = range.cloneContents();
document.body.appendChild(fragment);
```

ابتدا به خود گره پاراگراف و نیز گره فرزند _دوم_ درون پاراگراف ارجاع می‌گیریم. فرزند اول المان `<strong>` است. فرزند دوم text node با محتوای " is a paragraph." است.

با در دست داشتن ارجاع به text node، یک شیء `Range` جدید با فراخوانی `createRange()` روی خود `Document` می‌سازیم. موقعیت شروع محدوده را روی ششمین کاراکتر رشته text node و موقعیت پایان را روی طول رشته text node منهای یک تنظیم می‌کنیم. این کار محدوده را طوری تنظیم می‌کند که کلمه "paragraph" را در بر بگیرد.

سپس با فراخوانی `cloneContents()` روی `Range` یک شیء `DocumentFragment` جدید می‌سازیم که شامل بخشی از سند است که درون محدوده قرار دارد. پس از آن، با استفاده از `appendChild()` آن قطعه را به انتهای body سند، که از `document.body` به‌دست می‌آید، اضافه می‌کنیم.

## Specifications

## Browser compatibility