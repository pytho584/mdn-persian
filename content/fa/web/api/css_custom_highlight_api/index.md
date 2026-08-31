---
title: "CSS Custom Highlight API"
slug: Web/API/CSS_Custom_Highlight_API
page-type: web-api-overview
browser-compat:
  - api.Highlight
  - api.HighlightRegistry
  - css.selectors.highlight
spec-urls: https://drafts.csswg.org/css-highlight-api-1/
---

{{DefaultAPISidebar("CSS Custom Highlight API")}}

CSS Custom Highlight API سازوکاری برای استایل‌دهی به بازه‌های متنی دلخواه در یک سند فراهم می‌کند، به گونه‌ای که با استفاده از جاوااسکریپت بازه‌ها را ایجاد کرده و با CSS آن‌ها را استایل می‌دهید.

## مفاهیم و کاربرد

استایل‌دهی به بازه‌های متنی در یک صفحه وب می‌تواند بسیار مفید باشد. برای مثال، برنامه‌های ویرایش متن وب، خطاهای املایی یا دستوری را برجسته می‌کنند و ویرایشگرهای کد نیز خطاهای نحوی را هایلایت می‌کنند.

CSS Custom Highlight API مفهوم شبه‌عنصر‌های هایلایت دیگر مانند {{cssxref('::selection')}}، {{cssxref('::spelling-error')}}، {{cssxref('::grammar-error')}} و {{cssxref('::target-text')}} را گسترش می‌دهد. این API راهی برای ایجاد و استایل‌دهی به اشیای {{domxref('Range')}} دلخواه فراهم می‌کند، به جای اینکه تنها به بازه‌های تعریف‌شده توسط مرورگر محدود باشید.

با استفاده از CSS Custom Highlight API می‌توانید برنامه‌نویسی (programmatically) بازه‌های متنی ایجاد کنید و آن‌ را بدون تأثیر بر ساختار DOM صفحه، برجسته (highlight) کنید.

برای استایل‌دهی به بازه‌های متنی در یک صفحه وب با استفاده از CSS Custom Highlight API چهار مرحله وجود دارد:

1. ایجاد اشیای {{domxref("Range")}}.
2. ایجاد اشیای {{domxref("Highlight")}} برای این بازه‌ها.
3. ثبت هایلایت‌ها با استفاده از {{domxref("HighlightRegistry")}}.
4. استایل‌دهی به هایلایت‌ها با استفاده از شبه‌عنصر {{cssxref("::highlight", "::highlight()")}}.

### ایجاد بازه‌ها

اولین قدم، تعریف بازه‌های متنی است که می‌خواهید با ایجاد اشیای {{domxref("Range")}} در جاوااسکریپت استایل دهید. برای مثال:

```js
const parentNode = document.getElementById("foo");

const range1 = new Range();
range1.setStart(parentNode, 10);
range1.setEnd(parentNode, 20);

const range2 = new Range();
range2.setStart(parentNode, 40);
range2.setEnd(parentNode, 60);
```

### ایجاد هایلایت‌ها

دومین قدم، نمونه‌سازی (instantiate) اشیای {{domxref("Highlight")}} برای بازه‌های متنی شماست.

می‌توان چندین بازه را به یک هایلایت مرتبط کرد. اگر می‌خواهید چندین بخش متن را به یک شکل هایلایت کنید، باید یک هایلایت واحد ایجاد کرده و آن را با بازه‌های مربوطه مقداردهی اولیه کنید.

```js
const highlight = new Highlight(range1, range2);
```

اما می‌توانید به تعداد نیاز هایلایت ایجاد کنید. برای مثال، اگر در حال ساختن یک ویرایشگر متن مشارکتی (collaborative) هستید که هر کاربر رنگ متنی متفاوتی دارد، می‌توانید به ازای هر کاربر یک هایلایت ایجاد کنید، همانطور که در قطعه کد زیر می‌بینید:

```js
const user1Highlight = new Highlight(user1Range1, user1Range2);
const user2Highlight = new Highlight(user2Range1, user2Range2, user2Range3);
```

هر هایلایت می‌تواند به صورت متفاوت استایل داده شود.

### ثبت هایلایت‌ها

پس از ایجاد هایلایت‌ها، آن‌ها را با استفاده از {{domxref("HighlightRegistry")}} که به عنوان {{domxref("CSS/highlights_static", "CSS.highlights")}} در دسترس است، ثبت کنید.

این رجیستری یک شیء شبیه به {{jsxref("Map")}} است که برای ثبت هایلایت‌ها با نام‌های مشخص استفاده می‌شود، همانطور که در زیر می‌بینید:

```js
CSS.highlights.set("user-1-highlight", user1Highlight);
CSS.highlights.set("user-2-highlight", user2Highlight);
```

در قطعه کد بالا، رشته‌های `"user-1-highlight"` و `"user-2-highlight"` شناسه‌های سفارشی هستند که می‌توان در CSS برای اعمال استایل به هایلایت‌های ثبت‌شده استفاده کرد.

می‌توانید به تعداد نیاز هایلایت در رجیستری ثبت کنید، همچنین هایلایت‌ها را حذف کرده و کل رجیستری را پاک کنید.

```js
// Remove a single highlight from the registry.
CSS.highlights.delete("user-1-highlight");

// Clear the registry.
CSS.highlights.clear();
```

### استایل‌دهی به هایلایت‌ها

آخرین مرحله، استایل‌دهی به هایلایت‌های ثبت‌شده است. این کار با استفاده از شبه‌عنصر {{cssxref("::highlight", "::highlight()")}} انجام می‌شود. برای مثال، برای استایل‌دهی به هایلایت `"user-1-highlight"` که در مرحله قبل ثبت شده است:

```css
::highlight(user-1-highlight) {
  background-color: yellow;
  color: black;
}
```

## رابط‌ها (Interfaces)

- {{domxref("Highlight")}}
  - : این رابط برای نمایش مجموعه‌ای از بازه‌ها که باید در یک سند استایل داده شوند، استفاده می‌شود.
- {{domxref("HighlightRegistry")}}
  - : که از طریق {{domxref("CSS/highlights_static", "CSS.highlights")}} قابل دسترسی است، این شیء شبیه به {{jsxref("Map")}} برای ثبت هایلایت‌ها با شناسه‌های سفارشی استفاده می‌شود.

## نمونه‌ها

### هایلایت کردن نتایج جستجو

این نمونه نشان می‌دهد که چگونه از CSS Custom Highlight API برای هایلایت کردن نتایج جستجو استفاده کنید.

#### HTML

قطعه کد HTML زیر یک فیلد جستجو و یک مقاله با چند پاراگراف متن را تعریف می‌کند:

```html
<label>Search within text <input id="query" type="text" /></label>
<article>
  <p>
    Maxime debitis hic, delectus perspiciatis laborum molestiae labore,
    deleniti, quam consequatur iure veniam alias voluptas nisi quo. Dolorem
    eaque alias, quo vel quas repudiandae architecto deserunt quidem, sapiente
    laudantium nulla.
  </p>
  <p>
    Maiores odit molestias, necessitatibus doloremque dolor illum reprehenderit
    provident nostrum laboriosam iste, tempore perferendis! Ab porro neque esse
    voluptas libero necessitatibus fugiat, ex, minus atque deserunt veniam
    molestiae tempora? Vitae.
  </p>
  <p>
    Dolorum facilis voluptate eaque eius similique ducimus dignissimos assumenda
    quos architecto. Doloremque deleniti non exercitationem rerum quam alias
    harum, nisi obcaecati corporis temporibus vero sapiente voluptatum est
    quibusdam id ipsa.
  </p>
</article>
```

#### JavaScript

از جاوااسکریپت برای گوش دادن به رویداد `input` روی فیلد جستجو استفاده می‌شود. هنگامی که رویداد رخ می‌دهد، کد به دنبال تطابق‌های متن ورودی در متن مقاله می‌گردد. سپس برای این تطابق‌ها بازه‌هایی ایجاد می‌کند و با استفاده از CSS Custom Highlight API یک شیء هایلایت به نام `"search-results"` ایجاد و ثبت می‌کند:

```js
const query = document.getElementById("query");
const article = document.querySelector("article");

// Find all text nodes in the article. We'll search within
// these text nodes.
const treeWalker = document.createTreeWalker(article, NodeFilter.SHOW_TEXT);
const allTextNodes = [];
let currentNode = treeWalker.nextNode();
while (currentNode) {
  allTextNodes.push(currentNode);
  currentNode = treeWalker.nextNode();
}

// Listen to the input event to run the search.
query.addEventListener("input", () => {
  // If the CSS Custom Highlight API is not supported,
  // display a message and bail-out.
  if (!CSS.highlights) {
    article.textContent = "CSS Custom Highlight API not supported.";
    return;
  }

  // Clear the HighlightRegistry to remove the
  // previous search results.
  CSS.highlights.clear();

  // Clean-up the search query and bail-out if
  // if it's empty.
  const str = query.value.trim().toLowerCase();
  if (!str) {
    return;
  }

  // Iterate over all text nodes and find matches.
  const ranges = allTextNodes
    .map((el) => ({ el, text: el.textContent.toLowerCase() }))
    .map(({ text, el }) => {
      const indices = [];
      let startPos = 0;
      while (startPos < text.length) {
        const index = text.indexOf(str, startPos);
        if (index === -1) break;
        indices.push(index);
        startPos = index + str.length;
      }

      // Create a range object for each instance of
      // str we found in the text node.
      return indices.map((index) => {
        const range = new Range();
        range.setStart(el, index);
        range.setEnd(el, index + str.length);
        return range;
      });
    });

  // Create a Highlight object for the ranges.
  const searchResultsHighlight = new Highlight(...ranges.flat());

  // Register the Highlight object in the registry.
  CSS.highlights.set("search-results", searchResultsHighlight);
});
```

#### CSS

در نهایت، شبه‌عنصر `::highlight()` در CSS برای استایل‌دهی به هایلایت‌ها استفاده می‌شود:

```css
::highlight(search-results) {
  background-color: #ff0066;
  color: white;
}
```

#### نتیجه

نتیجه در زیر نشان داده شده است. متنی را در فیلد جستجو تایپ کنید تا تطابق‌های موجود در مقاله هایلایت شوند:

{{ EmbedLiveSample('Highlighting search results', 700, 300) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی HTML [`contentEditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable)
- CSS {{cssxref("pseudo-elements")}}
- ماژول [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API)
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/) از CSS-Tricks (2022)