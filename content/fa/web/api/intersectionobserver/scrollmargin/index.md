---
title: "IntersectionObserver: scrollMargin property"
short-title: scrollMargin
slug: Web/API/IntersectionObserver/scrollMargin
page-type: web-api-instance-property
browser-compat: api.IntersectionObserver.scrollMargin
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط‑خواندنی **`scrollMargin`** در رابط {{domxref("IntersectionObserver")}} یک حاشیه به تمام {{glossary("scroll container","ظرف‌های پیمایش")}} تو در توی داخل عنصر ریشه اضافه می‌کند، از جمله خود عنصر ریشه در صورتی که یک ظرف پیمایش باشد.

این کار باعث بزرگ یا کوچک شدن مستطیل برش ظرف‌های پیمایش‌شونده قبل از محاسبه تقاطع‌ها می‌شود.
برای مثال، به شما امکان می‌دهد مرزهای ظرف پیمایش را طوری تنظیم کنید که عنصر هدف حتی اگر پیکسل‌های آن هنوز در viewport ظرف نمایش داده نشده‌اند، قابل مشاهده در نظر گرفته شود، یا اگر لبه‌ای خیلی به لبه جعبه محدودکننده ظرف نزدیک باشد، هدف را تا حدی پنهان تلقی کنید.

توجه داشته باشید که اگر عنصر ریشه نیز یک ظرف پیمایش‌شونده باشد، آنگاه `scrollMargin` و {{domxref("IntersectionObserver/rootMargin","rootMargin")}} با هم ترکیب می‌شوند تا مستطیل محدودکننده مؤثر برای محاسبه تقاطع‌ها با هدف تعیین شود.

برای اطلاعات بیشتر به [ریشه تقاطع و حاشیه پیمایش](/en-US/docs/Web/API/Intersection_Observer_API#the_intersection_root_and_scroll_margin) در نمای کلی API مراجعه کنید.

## مقدار

یک رشته، مشابه مقدار ویژگی CSS {{cssxref("margin")}}.

حاشیه مشخص‌شده، افست‌هایی برای یک یا چند طرف مستطیل برش یک ظرف پیمایش تعریف می‌کند.
اگر `scrollMargin` هنگام نمونه‌سازی شیء مشخص نشده باشد، به طور پیش‌فرض به رشته `"0px 0px 0px 0px"` تنظیم می‌شود.

## مثال

### چرخ‌فلک (carousel) با حاشیه پیمایش

این مثال یک جعبه پیمایش‌شونده (عنصر ریشه) تعریف می‌کند که شامل یک چرخ‌فلک تصویر است که ابتدا خارج از دید قرار دارد.
یک observer روی عنصر ریشه، اهداف عنصر تصویر را درون چرخ‌فلک مشاهده می‌کند.
هنگامی که یک عنصر تصویر شروع به تقاطع با عنصر ریشه می‌کند، تصویر بارگذاری می‌شود، تقاطع ثبت می‌شود، و observer حذف می‌شود.

این مثال به شما امکان می‌دهد `scrollMargin` را تغییر دهید تا ببینید این تغییر چه زمانی باعث می‌شود اهداف درون ظرف پیمایش چرخ‌فلک شروع به تقاطع کنند.

#### HTML

```html hidden
<button id="reset" type="button">بازنشانی</button>
```

کد زیر عنصر `root-container` (یک {{htmlelement("div")}}) را تعریف می‌کند که از آن به عنوان عنصر ریشه observer تقاطع استفاده می‌کنیم.
این عنصر به نوبه خود شامل یک {{htmlelement("p")}} است که برای "به طور پیش‌فرض" خارج از دید قرار دادن سایر عناصر به کار می‌رود، یک `carousel` `<div>` و یک `margin-indicator` (برای نشان دادن اندازه حاشیه اعمال‌شده به عناصر پیمایش‌شونده درون عنصر ریشه).

عناصر {{htmlelement("img")}} درون چرخ‌فلک دارای یک ویژگی `data-src` هستند که شامل یک نام فایل است.
در کد observer خود، از این ویژگی برای تنظیم `img.src` زمانی که هر تصویر شروع به تقاطع با عنصر ریشه می‌کند، استفاده می‌کنیم که منجر به بارگذاری تصویر می‌شود.

```html
<div id="root-container">
  <p>محتوا قبل (به پایین بروید تا چرخ‌فلک را ببینید)</p>

  <div class="flex-container">
    <div class="carousel">
      <img
        src=""
        data-src="ballon-portrait.jpg"
        class="lazy-carousel-img"
        alt="Balloon portrait" />
      <img
        src=""
        data-src="balloon-small.jpg"
        class="lazy-carousel-img"
        alt="balloon-small" />
      <img
        src=""
        data-src="surfer.jpg"
        class="lazy-carousel-img"
        alt="surfer" />
      <img
        src=""
        data-src="border-diamonds.png"
        class="lazy-carousel-img"
        alt="border-diamonds" />
      <img src="" data-src="fire.png" class="lazy-carousel-img" alt="fire" />
      <img
        src=""
        data-src="puppy-header.jpg"
        class="lazy-carousel-img"
        alt="puppy" />
      <img src="" data-src="moon.jpg" class="lazy-carousel-img" alt="moon" />
      <img src="" data-src="rhino.jpg" class="lazy-carousel-img" alt="rhino" />
    </div>
    <div id="margin-indicator"></div>
  </div>
  <p>محتوا بعد</p>
</div>
```

```html
<div class="controls">
  <label>
    حاشیه سمت راست ریشه پیمایش را تنظیم کنید:
    <input id="margin" type="number" value="0" step="5" />px
  </label>
</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

```css
#root-container {
  height: 250px;
  overflow-y: auto;
  border: solid blue;
}

p {
  height: 50vh;
}

.flex-container {
  display: flex;
}

#margin-indicator {
  position: relative;
  height: 100px;
  width: 1px;
  background-color: red;
  opacity: 0.5;
  display: flex;
}

.carousel {
  width: 300px;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  display: flex;
  border: solid;
  /* outline: 200px solid rgba(0, 0, 0, 0.1); */
}
.carousel img {
  scroll-snap-stop: always;
  scroll-snap-align: start;
  display: block;
  width: 195px;
  height: 99px;
  min-width: 195px;
  min-height: 99px;
  margin-right: 10px;
  background-color: #eeeeee; /* Placeholder background */
}

.controls {
  margin-top: 10px;
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

#### JavaScript

```js hidden
const reload = document.querySelector("#reset");

reload.addEventListener("click", () => {
  window.location.reload(true);
});

const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

بخش اول کد تابع `createImageObserver()` را تعریف می‌کند که برای ایجاد اشیاء `IntersectionObserver` و اختصاص آن به متغیر `imageObserver` استفاده می‌کنیم.
از تابع استفاده می‌کنیم زیرا گزینه‌های observer پس از ساخته شدن قابل تغییر نیستند و می‌خواهیم تأثیر مقادیر مختلف `scrollMargin` را نشان دهیم.

`IntersectionObserver` با `rootMargin` صفر، `threshold` نزدیک به صفر، و یک `scrollMargin` که مقدار خود را از ورودی `margin` می‌گیرد و به تمام طرف‌های ظرف پیمایش اعمال می‌شود، ایجاد می‌شود.

تابع callback برای همه اهداف مشاهده‌شده فراخوانی می‌شود.
برای اهداف تقاطع‌یافته، `img.src` را به نام تصویری که باید بارگذاری شود (از `img.dataset.src`) تنظیم می‌کند، تقاطع را ثبت می‌کند، و سپس مشاهده تصویر را متوقف می‌کند.

کد انتهای تابع {{domxref("IntersectionObserver.observe()")}} را روی هر تصویر فراخوانی می‌کند تا observer شروع به کار کند.

```js
const rootContainer = document.getElementById("root-container");
const marginIndicator = document.getElementById("margin-indicator");
const carousel = document.querySelector(".carousel");
const lazyImages = carousel.querySelectorAll(".lazy-carousel-img");
let imageObserver;

function createImageObserver() {
  if (imageObserver) {
    imageObserver.disconnect();
  }

  let observerOptions = {
    root: rootContainer,
    rootMargin: "0px", // حاشیه اضافی ندارد
    scrollMargin: `${margin.valueAsNumber}px`, // حاشیه اضافی ندارد / قابل تنظیم است
    threshold: 0.01, // وقتی 1% از تصویر قابل مشاهده است فعال شود
  };

  imageObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const img = entry.target;
        log(`intersect: ${img.dataset.src}`); // فقط در اولین تقاطع
        img.src = `https://mdn.github.io/shared-assets/images/examples/${img.dataset.src}`; // بارگذاری تصویر با تنظیم src
        img.classList.remove("lazy-carousel-img"); // حذف کلاس
        observer.unobserve(img); // پس از بارگذاری، مشاهده را متوقف کن
      }
    });
  }, observerOptions);

  if (margin.valueAsNumber < 0) {
    marginIndicator.style.width = `${-margin.valueAsNumber}px`;
    marginIndicator.style.left = `${margin.valueAsNumber}px`;
    marginIndicator.style.backgroundColor = "blue";
  } else {
    marginIndicator.style.width = `${margin.valueAsNumber}px`;
    marginIndicator.style.left = "0px";
    marginIndicator.style.backgroundColor = "green";
  }

  lazyImages.forEach((image) => {
    imageObserver.observe(image); // شروع مشاهده هر تصویر
  });
}
```

کد زیر observer را با استفاده از `createImageObserver()` در شروع و هر بار که مقدار ورودی `margin` تغییر می‌کند، ایجاد می‌کند.
اگر رابط `IntersectionObserver` پشتیبانی نشود، همه تصاویر را بلافاصله بارگذاری می‌کند.

```js
if ("IntersectionObserver" in window) {
  createImageObserver();
  margin.addEventListener("input", () => {
    createImageObserver();
  });
} else {
  // Fallback for browsers that don't support Intersection Observer
  // Loads all images immediately if Intersection Observer is not supported.
  lazyImages.forEach((img) => {
    img.src = img.dataset.src;
    img.classList.remove("lazy-carousel-img");
  });
  console.warn(
    "Intersection Observer not supported. All carousel images loaded.",
  );
}
```

#### نتایج

به پایین بروید تا چرخ‌فلک نمایش داده شود. تصاویر قابل مشاهده باید بلافاصله بارگذاری شوند.
اگر چرخ‌فلک را به راست بکشید، باید مشاهده کنید که تصاویر به محض قابل مشاهده شدن عنصر بارگذاری می‌شوند.

می‌توانید از کنترل ارائه‌شده برای تغییر درصد حاشیه پیمایش (پس از بازنشانی مثال) استفاده کنید.
اگر یک مقدار مثبت مانند ۲۰px تنظیم کنید، مستطیل برش ظرف پیمایش به اندازه ۲۰px افزایش می‌یابد و باید مشاهده کنید که تصاویر قبل از اینکه در viewport ظاهر شوند، تشخیص داده شده و بارگذاری می‌شوند.
به طور مشابه، یک مقدار منفی به این معنی است که تقاطع زمانی تشخیص داده می‌شود که تصاویر از قبل در viewport هستند.

{{EmbedLiveSample("Carousel with scroll margin","100%","500px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}