---
title: "HTMLImageElement: sizes property"
short-title: sizes
slug: Web/API/HTMLImageElement/sizes
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.sizes
---

{{APIRef("HTML DOM")}}

ویژگی **`sizes`** در رابط {{domxref("HTMLImageElement")}} به شما امکان می‌دهد عرض چیدمان [تصویر](/en-US/docs/Web/HTML/Reference/Elements/img) را برای هر یک از فهرست [پرس‌وجوهای رسانه‌ای](/en-US/docs/Web/CSS/Guides/Media_queries) یا مقدار `auto` برای تصاویر با بارگذاری تأخیری (lazy-loaded) مشخص کنید تا مرورگر بتواند به‌صورت خودکار تصویری را بر اساس اندازه چیدمان عنصر برای نمایش انتخاب کند. این امکان به مرورگر می‌دهد تا بین تصاویر مختلف مشخص‌شده در {{domxref("HTMLImageElement/srcset", "srcset")}} عنصر، تصویری را که با شرایط رسانه‌ای متفاوت (حتی تصاویر با جهت‌گیری یا نسبت ابعاد متفاوت) هم‌خوانی دارد انتخاب کند.

ویژگی `sizes` نمایش‌دهندهٔ ویژگی محتوایی [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) عنصر `<img>` است. این ویژگی فقط زمانی می‌تواند وجود داشته باشد که `srcset` از توصیف‌گرهای عرض (width descriptors) استفاده کند.

## مقدار

یک رشته که می‌تواند کلیدواژهٔ `auto` (اختیاری و به‌دنبال آن هر تعداد _اندازهٔ منبع_) یا یک یا چند _اندازهٔ منبع_ باشد.

برای اطلاعات بیشتر، ویژگی [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) را در مرجع عنصر `<img>` اچ‌تی‌ام‌ال ببینید.

## مثال‌ها

### انتخاب تصویری که با عرض پنجره سازگار باشد

این مثال نشان می‌دهد که مرورگر چگونه از ویژگی `sizes` برای انتخاب تصویری از `srcset` بر اساس عرض رندر شدهٔ تصویر در عرض فعلی viewport استفاده می‌کند. همچنین به شما امکان می‌دهد تأثیر تغییر اندازهٔ پنجرهٔ مرورگر را بر تصویری که بارگذاری می‌شود مشاهده کنید.

#### HTML

برای نشان دادن اثر بارگذاری تأخیری، تصاویر ابتدا باید از {{glossary("visual viewport")}} پنهان باشند و سپس با اسکرول به دید درآیند. این کار با یک {{htmlelement("div")}} بیرونی با کلاس `scroll-container` انجام می‌شود که ظرف‌های `spacer` و `demo-wrap` را در خود جای می‌دهد. تصویر داخل ظرف `demo-wrap` قرار دارد که با ارتفاع تنظیم‌شده روی ظرف `spacer` به بیرون از دیدپذیری رانده می‌شود.

عنصر {{htmlelement("img")}} دارای ویژگی‌های زیر است:

- `srcset` چهار تصویر را تعریف می‌کند و نشان می‌دهد که عرض آن‌ها به ترتیب `600px`، `900px`، `1200px` و `1500px` است.
- `src` تصویری را مشخص می‌کند که اگر `srcset` پشتیبانی نشود یا قابل تجزیه نباشد استفاده خواهد شد. ما بزرگ‌ترین تصویر را در `srcset` استفاده می‌کنیم، زیرا تقریباً همیشه کاهش مقیاس آن بهتر از افزایش مقیاس کوچک‌ترین تصویر است.
- `loading` برابر با `lazy` است.
- `sizes` عرض رندر مورد انتظار تصویر را در مجموعه‌ای از نقاط شکست عرض viewport مشخص می‌کند و به مرورگر اجازه می‌دهد مناسب‌ترین تصویر را از `srcset` انتخاب کند.

```html
<div id="scroll-container">
  Scroll down to display images
  <div id="spacer"></div>
  <div id="demo-wrap">
    <div class="img-container" id="resizable">
      <div class="img-square">
        <img
          loading="lazy"
          sizes="(max-width: 600px) 600px, (max-width: 900px) 900px, (max-width: 1200px) 1200px, 1500px"
          src="1500.png"
          srcset="600.png 600w, 900.png 900w, 1200.png 1200w, 1500.png 1500w"
          alt="Example image" />
      </div>
      <div class="label">
        <strong>Container width: <span id="width-label"></span></strong>
      </div>
    </div>
  </div>
</div>
```

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```css hidden
#scroll-container {
  height: 600px;
  overflow-y: scroll;
  border: 2px solid #cccccc;
}
#spacer {
  height: 620px;
}
#demo-wrap {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  align-items: flex-start;
  padding: 16px;
}
.img-container {
  border: 2px solid #cccccc;
  overflow: hidden;
}
.img-square {
  width: 100%;
  aspect-ratio: 1 / 1;
  overflow: hidden;
}
.img-square img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.label {
  font-size: 13px;
  padding: 6px 10px;
  background: whitesmoke;
}
#resizable {
  width: 100%;
}
```

```js hidden
// Logging
const images = document.querySelectorAll(".img-square img");
const widthLabel = document.getElementById("width-label");

function updateWidthLabel() {
  widthLabel.textContent = `${document.getElementById("resizable").offsetWidth}px`;
}

updateWidthLabel();
new ResizeObserver(updateWidthLabel).observe(
  document.getElementById("resizable"),
);

images.forEach((img) => {
  if (img.complete) {
    log(`Already cached: ${img.currentSrc} (${img.offsetWidth}px)`);
  }
  img.addEventListener("load", () => {
    log(`Loaded: ${img.currentSrc} (${img.offsetWidth}px container)`);
  });
});

const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const img = entry.target;
        log(`Entered viewport: ${img.alt}`);
        observer.unobserve(img);
      }
    });
  },
  {
    root: document.getElementById("scroll-container"),
    rootMargin: "0px",
    threshold: 0.1,
  },
);

images.forEach((img) => observer.observe(img));
```

CSS و جاوااسکریپت نشان داده نشده‌اند (اگر می‌خواهید آن‌ها را بررسی کنید، گزینهٔ «Play» را انتخاب کنید تا کل مثال را در زمین بازی تعاملی (interactive playground) ببینید).

#### نتیجه

این مثال بهتر است در {{LiveSampleLink('Selecting an image to fit window width', 'viewed in its own window')}} مشاهده شود، تا بتوانید اندازه‌ها را به‌طور کامل تنظیم کنید و مثال به قاب حاوی خود محدود نباشد.

1. قاب را اسکرول کنید تا تصویر نمایش داده شود. برچسب پایین تصویر، عرض فعلی ظرف را نشان می‌دهد.
2. اندازهٔ پنجره را تغییر دهید — باید ببینید که تصویر در نقاط شکست پرس‌وجوی رسانه‌ای ویژگی `sizes` تغییر می‌کند.

   توجه داشته باشید که تصویر انتخاب‌شده ممکن است بزرگ‌تر از آن چیزی باشد که فقط عرض ظرف نشان می‌دهد. بسیاری از نمایشگرها (اگر نه اکثر آن‌ها) دارای [نسبت پیکسل دستگاه (DPR)](/en-US/docs/Web/API/Window/devicePixelRatio) بزرگ‌تر از یک هستند. برای رندر تصویری شارپ با تراکم پیکسل فیزیکی صفحه، مرورگر مقدار راهنمای `sizes` منطبق‌شده را در DPR ضرب می‌کند و سپس از `srcset` انتخاب می‌کند. برای مثال، در یک نمایشگر ۲× با viewport حدوداً ۵۰۰ پیکسل، راهنمای منطبق‌شده `600px` است، اما مرورگر به دنبال تصویری حدود ۱۲۰۰ پیکسل می‌گردد و `1200.png` را به‌عنوان نزدیک‌ترین اندازهٔ موجود انتخاب کرده و سپس آن را برای تناسب با فضای موجود مقیاس‌بندی می‌کند.

   > [!NOTE]
   > در نتیجه، برخی از تصاویر موجود در `srcset` ممکن است در یک نمایشگر خاص در برخی نقاط شکست قابل دسترسی نباشند و این موضوع ممکن است به مرورگر بستگی داشته باشد.

{{EmbedLiveSample("Selecting an image to fit window width", "", 600)}}

لاگ اطلاعاتی را هنگام رویداد `load` برای تصویر و زمانی که تصویر با viewport مرئی تلاقی می‌کند فراهم می‌کند. توجه داشته باشید که تصویر به‌صورت تأخیری بارگذاری می‌شود، بنابراین رویداد `load` باید درست قبل از ورود تصویر به viewport رخ دهد.

### انتخاب خودکار تصویر برای تصاویر با بارگذاری تأخیری

این مثال نشان می‌دهد که تنظیم مقدار `sizes` روی `auto` چگونه بر انتخاب تصویری که از [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) بارگذاری می‌شود تأثیر می‌گذارد، در حالی که عناصر {{htmlelement("img")}} به‌صورت تأخیری بارگذاری می‌شوند. همچنین به شما امکان می‌دهد تأثیر تغییر اندازهٔ یک ظرف را بر تصویر بارگذاری‌شده مشاهده کنید.

#### HTML

HTML تقریباً مشابه مثال قبلی است، با این تفاوت که سه عنصر {{htmlelement("img")}} تقریباً یکسان تعریف می‌کند که هر کدام دارای یک `srcset` شامل سه تصویر با عرض‌های `600px`، `400px` و `200px` و مقدار `sizes` برابر با `auto` هستند. این تصاویر درون ظرف‌هایی قرار دارند که اندازهٔ آن‌ها به‌گونه‌ای تنظیم شده است که تصاویر مختلفی انتخاب شوند.

```html
<div id="scroll-container">
  Scroll down to display images
  <div id="spacer"></div>
  <div id="demo-wrap">
    <div class="img-container img-container--sm" id="resizable">
      <div class="img-square">
        <img
          loading="lazy"
          sizes="auto"
          src="600.png"
          srcset="600.png 600w, 400.png 400w, 200.png 200w"
          alt="Image in small container" />
      </div>
      <div class="label"><strong>Container width: 100px</strong></div>
    </div>

    <div class="img-container img-container--md">
      <div class="img-square">
        <img
          loading="lazy"
          sizes="auto"
          src="600.png"
          srcset="600.png 600w, 400.png 400w, 200.png 200w"
          alt="Image in medium container" />
      </div>
      <div class="label"><strong>Container width: 200px</strong></div>
    </div>

    <div class="img-container img-container--lg">
      <div class="img-square">
        <img
          loading="lazy"
          sizes="auto"
          src="600.png"
          srcset="600.png 600w, 400.png 400w, 200.png 200w"
          alt="Image in large container" />
      </div>
      <div class="label"><strong>Container width: 400px</strong></div>
    </div>
  </div>
</div>
```

```html hidden
<div id="controls">
  <label for="slider">First image width:</label>
  <input type="range" id="slider" min="100" max="700" value="100" step="1" />
  <input type="number" id="number" min="100" max="700" value="100" step="1" />
  <span>px</span>
</div>
```

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### CSS

در اینجا کلاس‌های CSS را نشان می‌دهیم که اندازهٔ ظرف‌های مختلف تصویر را تنظیم می‌کنند.

```css hidden
#scroll-container {
  height: 400px;
  overflow-y: scroll;
  border: 2px solid #cccccc;
}
#spacer {
  height: 600px;
}
#demo-wrap {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  align-items: flex-start;
  padding: 16px;
}
.img-container {
  border: 2px solid #cccccc;
  overflow: hidden;
}
.img-square {
  width: 100%;
  aspect-ratio: 1 / 1;
  overflow: hidden;
}
.img-square img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.label {
  font-size: 13px;
  padding: 6px 10px;
  background: whitesmoke;
}
```

```css hidden
#controls {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}
#number {
  width: 60px;
}
```

```css
.img-container--sm {
  width: 100px;
}
.img-container--md {
  width: 200px;
}
.img-container--lg {
  width: 400px;
}
```

```js hidden
const slider = document.getElementById("slider");
const number = document.getElementById("number");
const resizable = document.getElementById("resizable");
const resizableImg = resizable.querySelector("img");
const resizableLabel = resizable.querySelector(".label strong");

function setSize(px) {
  px = Math.min(700, Math.max(100, px));
  resizable.style.width = `${px}px`;
  resizableImg.sizes = `${px}px`; // update sizes so browser can pick new srcset candidate
  resizableLabel.textContent = `${px}px`;
  slider.value = px;
  number.value = px;
}

slider.addEventListener("input", () => setSize(slider.valueAsNumber));
number.addEventListener("input", () => setSize(number.valueAsNumber));

// Logging
const images = document.querySelectorAll(".img-square img");

images.forEach((img) => {
  if (img.complete) {
    log(`Already cached: ${img.currentSrc} (${img.offsetWidth}px)`);
  }
  img.addEventListener("load", () => {
    log(`Loaded: ${img.currentSrc} (${img.offsetWidth}px container)`);
  });
});

const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const img = entry.target;
        log(`Entered viewport: ${img.alt}`);
        observer.unobserve(img);
      }
    });
  },
  {
    root: document.getElementById("scroll-container"),
    rootMargin: "0px",
    threshold: 0.1,
  },
);

images.forEach((img) => observer.observe(img));
```

باقی‌ماندهٔ CSS و جاوااسکریپتی که اسلایدر، ثبت گزارش (logging) و غیره را مدیریت می‌کند نشان داده نشده است (اگر علاقه‌مند به بررسی آن‌ها هستید، گزینهٔ «Play» را انتخاب کنید تا کل مثال را در زمین بازی تعاملی ببینید).

#### نتیجه

قاب را اسکرول کنید تا سه تصویر نمایش داده شوند. مرورگر باید بر اساس محدودیت‌های مختلف عرض، تصویر متفاوتی برای هر یک انتخاب کرده باشد. می‌توانید با اسلایدر اندازهٔ ظرف تصویر اول را تغییر دهید. توجه داشته باشید که ممکن است مرورگر با تغییر اندازهٔ ظرف، تصویر جدیدی را برای نمایش انتخاب کند یا نکند، زیرا پیاده‌سازی‌ها ملزم به واکنش به تغییرات پویا نیستند.

{{EmbedLiveSample("Automatic image selection for lazy loaded images", "", 600)}}

لاگ اطلاعاتی را هنگام رویداد `load` برای هر تصویر و زمانی که تصویر با viewport مرئی تلاقی می‌کند فراهم می‌کند. توجه داشته باشید که تصاویر به‌صورت