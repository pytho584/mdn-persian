---
title: Location
slug: Web/API/Location
page-type: web-api-interface
browser-compat: api.Location
---

{{APIRef("HTML DOM")}}

رابط **`Location`** نشانی (URL) شیءِ متصل به خود را نشان می‌دهد. هر تغییری که روی آن اعمال شود، در شیءِ مرتبط با آن بازتاب می‌یابد. هر دو رابط {{domxref("Document")}} و {{domxref("Window")}} دارای چنین `Location` متصلی هستند که به‌ترتیب از طریق {{domxref("Document.location")}} و {{domxref("Window.location")}} در دسترس است.

## ساختار Location

نشانگر ماوس را روی بخش‌های مختلف URL زیر ببرید تا معنای هر یک نمایان شود:

```html hidden
<span id="href" title="href"
  ><span id="origin" title="origin"
    ><span id="protocol" title="protocol">https:</span>//<span
      id="host"
      title="host"
      ><span id="hostname" title="hostname">example.org</span>:<span
        id="port"
        title="port"
        >8080</span
      ></span
    ></span
  ><span id="pathname" title="pathname">/foo/bar</span
  ><span id="search" title="search">?q=baz</span
  ><span id="hash" title="hash">#bang</span></span
>
```

```css hidden
html {
  display: table;
  width: 100%;
}

body {
  display: table-cell;
  text-align: center;
  vertical-align: middle;
  font-family: "Georgia";
  font-size: 200%;
  line-height: 1em;
  white-space: nowrap;
}

[title] {
  position: relative;
  display: inline-block;
  box-sizing: border-box;
  line-height: 2em;
  cursor: pointer;
  color: gray;
}

[title]::before {
  content: attr(title);
  font-family: monospace;
  position: absolute;
  top: 100%;
  width: 100%;
  left: 50%;
  margin-left: -50%;
  font-size: 50%;
  line-height: 1.5;
  background: black;
}

[title]:hover::before,
:target::before {
  background: black;
  color: yellow;
}

[title] [title]::before {
  margin-top: 1.5em;
}

[title] [title] [title]::before {
  margin-top: 3em;
}

[title] [title] [title] [title]::before {
  margin-top: 4.5em;
}

[title]:hover,
:target {
  position: relative;
  z-index: 1;
  outline: 50em solid rgb(255 255 255 / 80%);
}
```

```js hidden
document.body.addEventListener("click", (event) => {
  event.preventDefault();

  window.location.hash = event.target.hasAttribute("id")
    ? `#${event.target.getAttribute("id")}`
    : "";
});
```

{{EmbedLiveSample('Location anatomy', '85ch', '180px')}}

## ویژگی‌های نمونه

- {{domxref("Location.ancestorOrigins")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMStringList")}} ایستا که به ترتیب معکوس، مبدأهای همهٔ بافت‌های مرورِ بالادستِ سندِ مرتبط با شیء `Location` مفروض را در بر می‌گیرد.
- {{domxref("Location.href")}}
  - : یک {{Glossary("stringifier")}} که رشته‌ای شامل کل URL را برمی‌گرداند. اگر مقدار آن تغییر کند، سندِ مرتبط به صفحهٔ جدید هدایت می‌شود. می‌توان آن را از مبدأی متفاوت با مبدأِ سندِ مرتبط نیز تنظیم کرد.
- {{domxref("Location.protocol")}}
  - : رشته‌ای شامل پروتکل (scheme) URL، از جمله `':'` انتهایی.
- {{domxref("Location.host")}}
  - : رشته‌ای که host را در بر می‌گیرد؛ یعنی _hostname_ (نام میزبان)، یک `':'` و _port_ (پورت) مربوط به URL.
- {{domxref("Location.hostname")}}
  - : رشته‌ای شامل دامنهٔ URL.
- {{domxref("Location.port")}}
  - : رشته‌ای شامل شمارهٔ پورت URL.
- {{domxref("Location.pathname")}}
  - : رشته‌ای شامل یک `'/'` آغازین و سپس مسیر URL، بدونِ در نظر گرفتن query string یا fragment.
- {{domxref("Location.search")}}
  - : رشته‌ای شامل یک `'?'` و سپس پارامترها یا «query string» (رشتهٔ جست‌وجو) URL. مرورگرهای مدرن [`URLSearchParams`](/en-US/docs/Web/API/URLSearchParams/get) و [`URL.searchParams`](/en-US/docs/Web/API/URL/searchParams) را فراهم می‌کنند تا تجزیهٔ پارامترهای query string آسان باشد.
- {{domxref("Location.hash")}}
  - : رشته‌ای شامل یک `'#'` و سپس شناسهٔ fragment در URL.
- {{domxref("Location.origin")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل شکل متعارفِ مبدأِ آن موقعیت خاص را برمی‌گرداند.

## متدهای نمونه

- {{domxref("Location.assign()")}}
  - : منبع موجود در URL داده‌شده به‌عنوان پارامتر را بارگذاری می‌کند.
- {{domxref("Location.reload()")}}
  - : URL کنونی را مجدداً بارگذاری می‌کند؛ درست مانند دکمهٔ Refresh.
- {{domxref("Location.replace()")}}
  - : منبع فعلی را با منبع موجود در URL داده‌شده جایگزین می‌کند (به آن URL هدایت می‌شود). تفاوت آن با متد `assign()` و تنظیم ویژگی `href` این است که پس از استفاده از `replace()`، صفحهٔ کنونی در تاریخچهٔ نشست ({{domxref("History")}}) ذخیره نمی‌شود؛ بنابراین کاربر نمی‌تواند با دکمهٔ _بازگشت_ به آن بازگردد.
- {{domxref("Location.toString()")}}
  - : رشته‌ای شامل کل URL را برمی‌گرداند. این متد مترادفی برای {{domxref("Location.href")}} است، اما نمی‌توان از آن برای تغییر مقدار استفاده کرد.

## مثال‌ها

```js
// location: https://developer.mozilla.org:8080/en-US/search?q=URL#search-results-close-container
const loc = document.location;
console.log(loc.href); // https://developer.mozilla.org:8080/en-US/search?q=URL#search-results-close-container
console.log(loc.protocol); // https:
console.log(loc.host); // developer.mozilla.org:8080
console.log(loc.hostname); // developer.mozilla.org
console.log(loc.port); // 8080
console.log(loc.pathname); // /en-US/search
console.log(loc.search); // ?q=URL
console.log(loc.hash); // #search-results-close-container
console.log(loc.origin); // https://developer.mozilla.org:8080

location.assign("http://another.site"); // load another page
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- دو ویژگی از `Location`: {{domxref("Window.location")}} و {{domxref("Document.location")}}.
- رابط‌های کار با URL: {{domxref("URL")}} و {{domxref("URLSearchParams")}}.