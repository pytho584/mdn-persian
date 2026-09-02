---
title: Intersection Observer API
slug: Web/API/Intersection_Observer_API
page-type: web-api-overview
browser-compat: api.IntersectionObserver
---

{{DefaultAPISidebar("Intersection Observer API")}}

API Intersection Observer روشی برای مشاهده‌ی ناهمگام تغییرات در تقاطع یک عنصر هدف با یک عنصر ancestor (جد) یا با {{Glossary("viewport")}} (نمای دید) سند سطح بالا فراهم می‌کند.

## نمای کلی

از لحاظ تاریخی، تشخیص دید یک عنصر، یا دید نسبی دو عنصر نسبت به یکدیگر، کاری دشوار بوده که راه‌حل‌های آن غیرقابل اعتماد بوده و باعث کندی مرورگر و وب‌سایت‌هایی که کاربر به آن‌ها دسترسی دارد می‌شده است. با بالغ شدن وب، نیاز به این نوع اطلاعات افزایش یافته است. اطلاعات مربوط به تقاطع به دلایل زیادی مورد نیاز است، از جمله:

- بارگذاری تنبل (Lazy-loading) تصاویر یا محتوای دیگر هنگام اسکرول شدن صفحه.
- پیاده‌سازی وب‌سایت‌های "پیمایش بی‌نهایت" که در آن با اسکرول کردن، محتوای بیشتر و بیشتری بارگذاری و رندر می‌شود تا کاربر مجبور به ورق زدن صفحات نباشد.
- گزارش‌دهی دید تبلیغات برای محاسبه درآمد تبلیغات.
- تصمیم‌گیری در مورد انجام یا عدم انجام وظایف یا فرآیندهای انیمیشن بر اساس اینکه آیا کاربر نتیجه را خواهد دید یا خیر.

در گذشته، پیاده‌سازی تشخیص تقاطع شامل event handlerها و حلقه‌هایی بود که متدهایی مانند {{domxref("Element.getBoundingClientRect()")}} را برای جمع‌آوری اطلاعات مورد نیاز برای هر عنصر تحت تأثیر فراخوانی می‌کردند. از آنجایی که تمام این کدها روی نخ اصلی (main thread) اجرا می‌شوند، حتی یکی از آن‌ها می‌تواند مشکلات عملکردی ایجاد کند. وقتی یک وب‌سایت با این تست‌ها بارگذاری می‌شود، اوضاع می‌تواند واقعاً آشفته شود.

یک صفحه وب را در نظر بگیرید که از پیمایش بی‌نهایت استفاده می‌کند. این صفحه از یک کتابخانه شخص ثالث برای مدیریت تبلیغات که به صورت دوره‌ای در سراسر صفحه قرار می‌گیرند استفاده می‌کند، گرافیک‌های متحرکی اینجا و آنجا دارد، و از یک کتابخانه سفارشی استفاده می‌کند که کادرهای اعلان و موارد مشابه را رسم می‌کند. هر یک از این موارد روال‌های تشخیص تقاطع مخصوص خود را دارند که همگی روی نخ اصلی اجرا می‌شوند. نویسنده وب‌سایت ممکن است حتی متوجه این موضوع نباشد، زیرا ممکن است اطلاعات کمی در مورد عملکرد داخلی دو کتابخانه‌ای که استفاده می‌کند داشته باشد. همانطور که کاربر در صفحه اسکرول می‌کند، این روال‌های تشخیص تقاطع به طور مداوم در طول کد مدیریت اسکرول فعال می‌شوند و در نتیجه تجربه‌ای ایجاد می‌شود که کاربر را از مرورگر، وب‌سایت و رایانه خود ناامید می‌کند.

API Intersection Observer به کد این امکان را می‌دهد که یک تابع callback (تابع بازگشتی) ثبت کند که هر زمان یک عنصر خاص وارد یا خارج از تقاطع با عنصر دیگری (یا {{Glossary("viewport")}}) می‌شود، یا زمانی که تقاطع بین دو عنصر به مقدار مشخصی تغییر می‌کند، اجرا شود. به این ترتیب، وب‌سایت‌ها دیگر نیازی به انجام هیچ کاری روی نخ اصلی برای نظارت بر این نوع تقاطع عناصر ندارند، و مرورگر آزاد است که مدیریت تقاطع‌ها را به دلخواه خود بهینه‌سازی کند.

یک کاری که API Intersection Observer نمی‌تواند انجام دهد: راه‌اندازی منطق بر اساس تعداد دقیق پیکسل‌های همپوشانی، یا به طور خاص بر اساس اینکه آن‌ها کدام‌اند. این API فقط مورد استفاده رایج "اگر آنها حدوداً _N_ درصد با هم تقاطع دارند، من باید کاری انجام دهم" را حل می‌کند.

## مفاهیم و کاربرد

API Intersection Observer به شما امکان می‌دهد یک callback را طوری پیکربندی کنید که در هر یک از شرایط زیر فراخوانی شود:

- یک عنصر **هدف** یا با viewport دستگاه یا با یک عنصر مشخص شده تقاطع پیدا کند. آن عنصر مشخص شده برای اهداف API Intersection Observer، **عنصر ریشه (root element)** یا **ریشه (root)** نامیده می‌شود.
- اولین باری که observer در ابتدا برای تماشای یک عنصر هدف درخواست می‌شود.

به طور معمول، شما می‌خواهید تغییرات تقاطع را با توجه به نزدیک‌ترین ancestor قابل اسکرول عنصر هدف، یا اگر عنصر هدف از نوادگان یک عنصر قابل اسکرول نباشد، viewport دستگاه را زیر نظر بگیرید. برای تماشای تقاطع نسبت به viewport دستگاه، `null` را برای گزینه `root` مشخص کنید. برای توضیح دقیق‌تر در مورد گزینه‌های observer تقاطع، به ادامه مطلب مراجعه کنید.

چه از viewport استفاده کنید و چه از عنصر دیگری به عنوان ریشه، API به یک شکل کار می‌کند و یک تابع callback که شما ارائه می‌دهید را هر زمان که دید عنصر هدف به گونه‌ای تغییر کند که از مقادیر مورد نظر تقاطع با ریشه عبور کند، اجرا می‌کند.

درجه تقاطع بین عنصر هدف و ریشه آن، **نسبت تقاطع (intersection ratio)** نامیده می‌شود. این مقدار نمایشی از درصد دید عنصر هدف به صورت یک عدد بین 0.0 و 1.0 است.

### ایجاد یک observer تقاطع

observer تقاطع را با فراخوانی سازنده آن و ارسال یک تابع callback که در هر بار عبور از یک threshold (آستانه) در یک جهت یا جهت دیگر اجرا می‌شود، ایجاد کنید:

```js
const options = {
  root: document.querySelector("#scrollArea"),
  rootMargin: "0px",
  scrollMargin: "0px",
  threshold: 1.0,
};

const observer = new IntersectionObserver(callback, options);
```

threshold برابر 1.0 به این معنی است که وقتی 100% از هدف در داخل عنصر مشخص شده توسط گزینه `root` قابل مشاهده است، callback فراخوانی می‌شود.

#### گزینه‌های observer تقاطع

شی `options` که به سازنده {{domxref("IntersectionObserver.IntersectionObserver", "IntersectionObserver()")}} ارسال می‌شود به شما امکان می‌دهد شرایطی را که تحت آن callback observer فراخوانی می‌شود کنترل کنید. این شی فیلدهای زیر را دارد:

- `root`
  - : عنصری که به عنوان viewport برای بررسی دید هدف استفاده می‌شود. باید ancestor هدف باشد. اگر مشخص نشود یا `null` باشد، به طور پیش‌فرض از viewport مرورگر استفاده می‌کند.
- `rootMargin`
  - : حاشیه (margin) اطراف ریشه. یک رشته از یک تا چهار مقدار مشابه ویژگی CSS {{cssxref("margin")}}، به عنوان مثال `"10px 20px 30px 40px"` (بالا، راست، پایین، چپ). مقادیر فقط می‌توانند بر حسب پیکسل (`px`) یا درصد (`%`) باشند. این مجموعه مقادیر برای بزرگ یا کوچک کردن هر طرف از جعبه محدودکننده عنصر ریشه قبل از محاسبه تقاطع‌ها استفاده می‌شود. مقادیر منفی جعبه محدودکننده عنصر ریشه را کوچک می‌کند و مقادیر مثبت آن را بزرگ می‌کند. مقدار پیش‌فرض، در صورت عدم مشخص شدن، `"0px 0px 0px 0px"` است.
- `scrollMargin`
  - : حاشیه اطراف {{glossary("scroll container","containers اسکرول")}} تو در تو که همان مقادیر/مقدار پیش‌فرض `rootMargin` را می‌گیرد. حاشیه‌ها قبل از محاسبه تقاطع‌ها روی containerهای قابل اسکرول تو در تو اعمال می‌شوند. مقادیر مثبت مستطیل برش container را بزرگ می‌کنند و به هدف‌ها اجازه می‌دهند قبل از قابل مشاهده شدن تقاطع داشته باشند، در حالی که مقادیر منفی مستطیل برش را کوچک می‌کنند.
- `threshold`
  - : یک عدد یا آرایه‌ای از اعداد که نشان می‌دهد در چه درصدی از دید عنصر هدف، callback observer باید اجرا شود. اگر فقط می‌خواهید زمانی که دید از مرز 50% عبور می‌کند تشخیص دهید، می‌توانید از مقدار 0.5 استفاده کنید. اگر می‌خواهید callback هر بار که دید 25% دیگر عبور می‌کند اجرا شود، آرایه \[0, 0.25, 0.5, 0.75, 1] را مشخص می‌کنید. مقدار پیش‌فرض 0 است (به این معنی که callback به محض اینکه عنصر هدف با مرز ریشه تقاطع یا تماس پیدا کند، حتی اگر هیچ پیکسلی هنوز قابل مشاهده نباشد، اجرا می‌شود). مقدار 1.0 به این معنی است که threshold تا زمانی که هر پیکسل قابل مشاهده نباشد عبور کرده محسوب نمی‌شود.
- `delay` {{experimental_inline}}
  - : هنگام ردیابی دید هدف ([trackVisibility](#trackvisibility) `true` است)، می‌توان از این برای تنظیم حداقل تأخیر بر حسب میلی‌ثانیه بین اعلان‌های این observer استفاده کرد. محدود کردن نرخ اعلان مطلوب است زیرا محاسبه دید از نظر محاسباتی سنگین است. اگر ردیابی دید فعال باشد، برای هر مقدار کمتر از 100، مقدار روی 100 تنظیم می‌شود و باید از بزرگترین مقدار قابل تحمل استفاده کنید. مقدار به طور پیش‌فرض 0 است.
- `trackVisibility` {{experimental_inline}}
  - : یک boolean که نشان می‌دهد آیا این `IntersectionObserver` در حال ردیابی تغییرات در دید یک هدف است یا خیر. وقتی `false` است، مرورگر تقاطع‌ها را زمانی گزارش می‌دهد که عنصر هدف به viewport عنصر ریشه اسکرول شود. وقتی `true` است، مرورگر علاوه بر این بررسی می‌کند که هدف واقعاً قابل مشاهده است و توسط عناصر دیگر پوشانده نشده یا به طور بالقوه توسط یک فیلتر، opacity کاهش یافته، یا transform تحریف یا پنهان نشده باشد. مقدار به طور پیش‌فرض `false` است زیرا ردیابی دید از نظر محاسباتی سنگین است. اگر این مقدار تنظیم شود، باید [`delay`](#delay) نیز تنظیم شود.

#### Callbackهای تغییر تقاطع

callback ارسال شده به سازنده `IntersectionObserver()` یک لیست از اشیاء {{domxref("IntersectionObserverEntry")}} و خود observer را دریافت می‌کند:

```js
const callback = (entries, observer) => {
  entries.forEach((entry) => {
    // هر ورودی یک تغییر تقاطع را برای یک عنصر هدف مشاهده شده توصیف می‌کند:
    //   entry.boundingClientRect
    //   entry.intersectionRatio
    //   entry.intersectionRect
    //   entry.isIntersecting
    //   entry.rootBounds
    //   entry.target
    //   entry.time
  });
};
```

لیست ورودی‌های دریافت شده توسط callback شامل یک شی {{domxref("IntersectionObserverEntry")}} برای هر رویداد عبور از threshold است – چندین ورودی می‌توانند در یک زمان دریافت شوند، یا از چندین هدف یا از یک هدف واحد که در مدت زمان کوتاهی از چندین threshold عبور می‌کند. ورودی‌ها با استفاده از یک صف (queue) ارسال می‌شوند، بنابراین باید بر اساس زمان تولید مرتب شوند، اما ترجیحاً از {{domxref("IntersectionObserverEntry.time")}} برای مرتب‌سازی صحیح آن‌ها استفاده کنید. هر ورودی توضیح می‌دهد که چه مقدار از یک عنصر معین با عنصر ریشه تقاطع دارد، آیا عنصر تقاطع‌دار محسوب می‌شود یا خیر، و غیره. ورودی فقط حاوی اطلاعات مربوط به آن لحظه خاص است – اگر به اطلاعاتی نیاز دارید که نیاز به ردیابی در طول زمان دارد، مانند جهت و سرعت اسکرول، ممکن است لازم باشد با به خاطر سپردن ورودی‌های قبلی خودتان آن را محاسبه کنید.

توجه داشته باشید که callback شما روی نخ اصلی اجرا می‌شود. باید در سریع‌ترین زمان ممکن عمل کند؛ اگر کار زمان‌بری نیاز است، از {{domxref("Window.requestIdleCallback()")}} استفاده کنید.

قطعه کد زیر یک callback را نشان می‌دهد که شمارشگر تعداد دفعاتی که عناصر از حالت عدم تقاطع با ریشه به حالت تقاطع حداقل 75% تغییر وضعیت می‌دهند را نگه می‌دارد. برای مقدار threshold 0.0 (پیش‌فرض)، callback تقریباً در هنگام تغییر مقدار boolean {{domxref("IntersectionObserverEntry.isIntersecting", "isIntersecting")}} فراخوانی می‌شود. بنابراین قطعه کد ابتدا بررسی می‌کند که تغییر وضعیت مثبت است، سپس تعیین می‌کند که آیا {{domxref("IntersectionObserverEntry.intersectionRatio", "intersectionRatio")}} بالای 75% است یا خیر، که در این صورت شمارنده را افزایش می‌دهد.

```js
const intersectionCallback = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      let elem = entry.target;

      if (entry.intersectionRatio >= 0.75) {
        intersectionCounter++;
      }
    }
  });
};
```

#### هدف‌گیری یک عنصر برای مشاهده

پس از ایجاد observer، باید یک عنصر هدف برای تماشا به آن بدهید:

```js
const target = document.querySelector("#listItem");
observer.observe(target);

// callback که برای observer تنظیم کرده‌ایم اکنون برای اولین بار اجرا می‌شود
// تا زمانی که یک هدف به observer خود اختصاص دهیم صبر می‌کند (حتی اگر هدف در حال حاضر قابل مشاهده نباشد)
```

هر زمان که هدف یک threshold مشخص شده برای `IntersectionObserver` را برآورده کند، callback فراخوانی می‌شود.

همچنین توجه داشته باشید که اگر گزینه `root` را مشخص کرده باشید، هدف باید از نوادگان عنصر ریشه باشد.

### نحوه محاسبه تقاطع

تمام نواحی در نظر گرفته شده توسط API Intersection Observer مستطیل هستند؛ عناصری که شکل نامنظم دارند به‌عنوان اشغال‌کننده کوچک‌ترین مستطیلی در نظر گرفته می‌شوند که تمام قسمت‌های عنصر را در بر می‌گیرد. به طور مشابه، اگر بخش قابل مشاهده یک عنصر مستطیلی نباشد، مستطیل تقاطع عنصر به عنوان کوچک‌ترین مستطیلی در نظر گرفته می‌شود که شامل تمام بخش‌های قابل مشاهده عنصر است.

درک کمی از نحوه توصیف یک تقاطع توسط ویژگی‌های مختلف ارائه شده توسط {{domxref("IntersectionObserverEntry")}} مفید است.

#### ریشه تقاطع و حاشیه ریشه

قبل از اینکه بتوانیم تقاطع یک عنصر با یک container را ردیابی کنیم، باید بدانیم آن container چیست. آن container **ریشه تقاطع (intersection root)** یا **عنصر ریشه (root element)** نامیده می‌شود. این می‌تواند یک عنصر خاص در سند باشد که ancestor عنصر مورد مشاهده است، یا `null` برای استفاده از viewport سند به عنوان container.

**_مستطیل تقاطع ریشه (root intersection rectangle)_** مستطیلی است که برای بررسی در برابر هدف یا اهداف استفاده می‌شود. این مستطیل به صورت زیر تعیین می‌شود:

- اگر ریشه تقاطع، ریشه ضمنی (یعنی {{domxref("Document")}} سطح بالا) باشد، مستطیل تقاطع ریشه، مستطیل viewport است.
- اگر ریشه تقاطع دارای overflow clip باشد، مستطیل تقاطع ریشه، ناحیه محتوای عنصر ریشه است.
- در غیر این صورت، مستطیل تقاطع ریشه، مستطیل bounding client عنصر ریشه است (که با فراخوانی {{domxref("Element.getBoundingClientRect", "getBoundingClientRect()")}} روی آن بازگردانده می‌شود).

مستطیل تقاطع ریشه را می‌توان با تنظیم **حاشیه ریشه (root margin)**، `rootMargin`، در هنگام ایجاد {{domxref("IntersectionObserver")}} بیشتر تنظیم کرد. مقادیر موجود در `rootMargin` offsetهایی را تعریف می‌کنند که به هر طرف از جعبه محدودکننده ریشه تقاطع اضافه می‌شوند تا مرزهای نهایی ریشه تقاطع (که در {{domxref("IntersectionObserverEntry.rootBounds")}} هنگام اجرای callback فاش می‌شوند) ایجاد شود. مقادیر مثبت جعبه را بزرگ می‌کنند، در حالی که مقادیر منفی آن را کوچک می‌کنند. هر مقدار offset فقط می‌تواند بر حسب پیکسل (px) یا درصد (%) بیان شود.

اثر بزرگ کردن جعبه با استفاده از حاشیه ریشه این است که به اهداف سرریز (overflow) اجازه می‌دهد قبل از قابل مشاهده شدن با ریشه تقاطع داشته باشند. برای مثال می‌توان از این برای شروع بارگذاری تصاویر درست قبل از اینکه در دید قرار گیرند استفاده کرد، نه در نقطه‌ای که قابل مشاهده می‌شوند.

در مثال زیر، یک جعبه قابل اسکرول و یک عنصر داریم که در ابتدا خارج از دید است. می‌توانید حاشیه سمت راست ریشه را تنظیم کنید و ببینید که:

- اگر حاشیه مثبت باشد، عنصر قرمز حتی اگر قابل مشاهده نباشد، به دلیل تقاطع با ناحیه حاشیه ریشه، دارای تقاطع با ریشه در نظر گرفته می‌شود.
- اگر حاشیه منفی باشد، حتی زمانی که عنصر قرمز شروع به قابل مشاهده شدن می‌کند، باز هم دارای تقاطع با ریشه در نظر گرفته نمی‌شود زیرا جعبه محدودکننده ریشه کوچک شده است.

```html hidden
<div class="demo">
  <div id="container">
    <div id="elem"></div>
    <div id="gutter"></div>
  </div>
  <div id="marginIndicator"></div>
</div>
<div class="controls">
  <label>
    حاشیه سمت راست ریشه را تنظیم کنید:
    <input id="margin" type="number" value="0" step="5" />px
  </label>
  <label>
    همچنین می‌توانید از این لغزنده برای اسکرول container استفاده کنید:
    <input id="scrollAmount" type="range" min="0" max="300" value="0" />
  </label>
  <p>نسبت تقاطع فعلی: <span id="output"></span></p>
</div>
```

```css hidden
.demo {
  display: flex;
}

.controls {
  display: flex;
  flex-direction: column;
}

#container {
  position: relative;
  width: 200px;
  height: 100px;
  overflow-x: scroll;
  border: 1px solid black;
}

#marginIndicator {
  position: relative;
  height: 100px;
  background-color: blue;
  opacity: 0.5;
}

#elem {
  background-color: red;
  width: 100px;
  height: 100px;
  position: absolute;
  left: 200px;
}

#gutter {
  width: 500px;
  height: 100px;
}
```

```js hidden
let observer;
function createObserver() {
  if (observer) {
    observer.disconnect();
  }
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        output.textContent = entry.intersectionRatio.toFixed(2);
      });
    },
    {
      threshold: Array.from({ length: 1000 }, (_, i) => i / 1000),
      root: container,
      rootMargin: `0px ${margin.value}px 0px 0px`,
    },
  );
  if (margin.valueAsNumber < 0) {
    marginIndicator.style.width = `${-margin.valueAsNumber}px`;
    marginIndicator.style.left = `${margin.valueAsNumber}px`;

    marginIndicator.style.backgroundColor = "blue";
  } else {
    marginIndicator.style.width = `${margin.valueAsNumber}px`;
    marginIndicator.style.left = "0px";
    marginIndicator.style.backgroundColor = "green";
  }
  observer.observe(elem);
}
createObserver();
margin.addEventListener("input", () => {
  createObserver();
});
scrollAmount.addEventListener("input", () => {
  container.scrollLeft = scrollAmount.value;
});
```

{{EmbedLiveSample("the intersection root and root margin", "", 200)}}

#### ریشه تقاطع و حاشیه اسکرول

موردی را در نظر بگیرید که یک عنصر ریشه دارید که شامل {{glossary("scroll container","containers اسکرول")}} تو در تو است و می‌خواهید تقاطع‌ها را با یک هدف درون یکی از آن containerهای قابل اسکرول مشاهده کنید. تقاطع با عنصر هدف به طور پیش‌فرض زمانی قابل مشاهده می‌شود که هدف در ناحیه تعریف شده توسط ریشه قابل مشاهده باشد؛ به عبارت دیگر، زمانی که container به داخل ریشه اسکرول می‌شود و هدف به داخل مستطیل برش container خود اسکرول می‌شود.

می‌توانید از حاشیه اسکرول (scroll margin) برای شروع مشاهده تقاطع‌ها قبل یا بعد از اسکرول شدن هدف به داخل viewport در container اسکرول آن استفاده کنید. این حاشیه به تمام containerهای اسکرول تو در تو در ریشه اضافه می‌شود، از جمله عنصر ریشه اگر خود نیز یک container اسکرول باشد، و اثر آن بزرگ کردن (حاشیه‌های مثبت) یا کوچک کردن (حاشیه منفی) ناحیه برش مورد استفاده برای محاسبه تقاطع‌ها است.

> [!NOTE]
> می‌توانید برای هر container اسکرول که می‌خواهید حاشیه اسکرول داشته باشد، یک observer تقاطع جداگانه ایجاد کنید و از ویژگی حاشیه ریشه برای دستیابی به یک اثر مشابه استفاده کنید. استفاده از حاشیه اسکرول ارگونومیک‌تر است، زیرا در بیشتر موارد می‌توانید فقط یک observer تقاطع برای همه اهداف تو در تو داشته باشید.

در مثال زیر، یک جعبه قابل اسکرول و یک گردونه تصویر که در ابتدا خارج از دید است داریم. یک observer روی عنصر ریشه، اهداف عنصر تصویر را در داخل گردونه مشاهده می‌کند. هنگامی که یک عنصر تصویر شروع به تقاطع با عنصر ریشه می‌کند، تصویر بارگذاری می‌شود، تقاطع ثبت می‌شود و observer حذف می‌شود.

برای نمایش گردونه به پایین اسکرول کنید. تصاویر قابل مشاهده باید بلافاصله بارگذاری شوند. اگر گردونه را اسکرول کنید، باید مشاهده کنید که تصاویر به محض قابل مشاهده شدن عنصر بارگذاری می‌شوند.

پس از بازنشانی مثال، می‌توانید از کنترل ارائه شده برای تغییر درصد حاشیه اسکرول استفاده کنید. اگر مقدار مثبتی مانند 20% تنظیم کنید، مستطیل برش container اسکرول به اندازه 20% افزایش می‌یابد و باید مشاهده کنید که تصاویر قبل از اینکه در دید قرار گیرند شناسایی و بارگذاری می‌شوند. به طور مشابه، یک مقدار منفی به این معنی است که تقاطع زمانی تشخیص داده می‌شود که تصاویر در حال حاضر در دید هستند.

```html hidden
<button id="reset" type="button">بازنشانی</button>
```

```html hidden
<div id="root-container">
  <p>محتوای قبل (برای گردونه به پایین اسکرول کنید)</p>

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
  <p>محتوای بعد</p>
</div>
```

```html hidden
<div class="controls">
  <label>
    حاشیه سمت راست ریشه اسکرول را تنظیم کنید:
    <input id="margin" type="number" value="0" step="5" />%
  </label>
</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#root-container {
  height: 250px;
  overflow-y: auto;
  border: solid blue;
}

.controls {
  margin-top: 10px;
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

#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

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

```js hidden
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
    rootMargin: "0px", // بدون حاشیه اضافی
    scrollMargin: `${margin.valueAsNumber}%`, // بدون حاشیه اضافی / قابل تنظیم
    threshold: 0.01, // زمانی که 1% از تصویر قابل مشاهده است فعال شود
  };

  imageObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const img = entry.target;
        log(`intersect: ${img.dataset.src}`); // فقط در اولین تقاطع
        img.src = `https://mdn.github.io/shared-assets/images/examples/${img.dataset.src}`; // بارگذاری تصویر با تنظیم src
        img.classList.remove("lazy-carousel-img"); // حذف کلاس
        observer.unobserve(img); // توقف مشاهده پس از بارگذاری
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

if ("IntersectionObserver" in window) {
  createImageObserver();
  margin.addEventListener("input", () => {
    createImageObserver();
  });
} else {
  // بازگشت به حالت عادی برای مرورگرهایی که از Intersection Observer پشتیبانی نمی‌کنند
  // در صورت عدم پشتیبانی، همه تصاویر بلافاصله بارگذاری می‌شوند.
  lazyImages.forEach((img) => {
    img.src = img.dataset.src;
    img.classList.remove("lazy-carousel-img");
  });
  console.warn(
    "Intersection Observer not supported. All carousel images loaded.",
  );
}
```

{{EmbedLiveSample("The intersection root and scroll margin","100%","500px")}}

#### آستانه‌ها (Thresholds)

API Intersection Observer به جای گزارش هر تغییر بی‌نهایت کوچک در میزان دید یک عنصر هدف، از **آستانه‌ها (thresholds)** استفاده می‌کند. هنگامی که یک observer ایجاد می‌کنید، می‌توانید یک یا چند مقدار عددی ارائه دهید که درصدهای قابل مشاهده بودن عنصر هدف را نشان می‌دهد. سپس، API فقط تغییرات در دید را که از این آستانه‌ها عبور می‌کنند گزارش می‌دهد.

به عنوان مثال، اگر می‌خواهید هر بار که دید یک هدف به جلو یا عقب از هر علامت 25% عبور می‌کند مطلع شوید، آرایه \[0, 0.25, 0.5, 0.75, 1] را به عنوان لیست آستانه‌ها هنگام ایجاد observer مشخص می‌کنید.

هنگامی که callback فراخوانی می‌شود، یک لیست از اشیاء `IntersectionObserverEntry` دریافت می‌کند، یکی برای هر هدف مشاهده شده که درجه تقاطع آن با ریشه به گونه‌ای تغییر کرده است که مقدار نمایان شده از یکی از آستانه‌ها، در هر جهت، عبور می‌کند.

می‌توانید با نگاه کردن به ویژگی {{domxref("IntersectionObserverEntry.isIntersecting", "isIntersecting")}} ورودی، ببینید که آیا هدف در حال _حاضر_ با ریشه تقاطع دارد یا خیر؛ اگر مقدار آن `true` باشد، هدف حداقل به صورت جزئی با عنصر ریشه یا سند تقاطع دارد. این به شما امکان می‌دهد تشخیص دهید که آیا ورودی نشان‌دهنده انتقال از حالت تقاطع عناصر به عدم تقاطع یا انتقال از عدم تقاطع به تقاطع است.

توجه داشته باشید که ممکن است یک مستطیل تقاطع صفر داشته باشیم، که می‌تواند اگر تقاطع دقیقاً در امتداد مرز بین آن دو باشد یا مساحت {{domxref("IntersectionObserverEntry.boundingClientRect", "boundingClientRect")}} صفر باشد، اتفاق بیفتد. این حالت اشتراک یک خط مرزی بین هدف و ریشه به اندازه کافی برای انتقال به حالت تقاطع در نظر گرفته نمی‌شود.

برای درک نحوه کار آستانه‌ها، سعی کنید جعبه زیر را جابجا کنید. هر جعبه رنگی داخل آن درصد دید خود را در هر چهار گوشه خود نمایش می‌دهد، بنابراین می‌توانید این نسبت‌ها را در طول زمان با اسکرول کردن container مشاهده کنید. هر جعبه مجموعه آستانه‌های متفاوتی دارد:

- جعبه اول برای هر درصد دید یک آستانه دارد؛ یعنی آرایه {{domxref("IntersectionObserver.thresholds")}} برابر است با `[0.00, 0.01, 0.02, /*…,*/ 0.99, 1.00]`.
- جعبه دوم یک آستانه واحد در علامت 50% دارد.
- جعبه سوم هر 10% دید آستانه دارد (0%، 10%، 20%، و غیره).
- جعبه آخر هر 25% آستانه دارد.

```html hidden
<template id="boxTemplate">
  <div class="sampleBox">
    <div class="label topLeft"></div>
    <div class="label topRight"></div>
    <div class="label bottomLeft"></div>
    <div class="label bottomRight"></div>
  </div>
</template>

<main>
  <div class="contents">
    <div class="wrapper"></div>
  </div>
</main>
```

```css hidden
.contents {
  position: absolute;
  width: 700px;
  height: 1725px;
}

.wrapper {
  position: relative;
  top: 600px;
}

.sampleBox {
  position: relative;
  left: 175px;
  width: 150px;
  background-color: rgb(245 170 140);
  border: 2px solid rgb(201 126 17);
  padding: 4px;
  margin-bottom: 6px;
}

#box1 {
  height: 200px;
}

#box2 {
  height: 75px;
}

#box3 {
  height: 150px;
}

#box4 {
  height: 100px;
}

.label {
  font:
    14px "Open Sans",
    "Arial",
    sans-serif;
  position: absolute;
  margin: 0;
  background-color: rgb(255 255 255 / 70%);
  border: 1px solid rgb(0 0 0 / 70%);
  width: 3em;
  height: 18px;
  padding: 2px;
  text-align: center;
}

.topLeft {
  left: 2px;
  top: 2px;
}

.topRight {
  right: 2px;
  top: 2px;
}

.bottomLeft {
  bottom: 2px;
  left: 2px;
}

.bottomRight {
  bottom: 2px;
  right: 2px;
}
```

```js hidden
let observers = [];

startup = () => {
  const wrapper = document.querySelector(".wrapper");
  const template = document.querySelector("#boxTemplate");

  // Options for the observers

  const observerOptions = {
    root: null,
    rootMargin: "0px",
    threshold: [],
  };

  // An array of threshold sets for each of the boxes. The
  // first box's thresholds are set programmatically
  // since there will be so many of them (for each percentage
  // point).

  const thresholdSets = [
    [],
    [0.5],
    [0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0],
    [0, 0.25, 0.5, 0.75, 1.0],
  ];

  for (let i = 0; i <= 1.0; i += 0.01) {
    thresholdSets[0].push(i);
  }

  // Add each box, creating a new observer for each

  for (let i = 0; i < 4; i++) {
    const newBox = document.importNode(template.content, true);
    const boxID = `box${i + 1}`;
    newBox.querySelector(".sampleBox").id = boxID;
    wrapper.appendChild(newBox);

    // Set up the observer for this box

    observerOptions.threshold = thresholdSets[i];
    observers[i] = new IntersectionObserver(
      intersectionCallback,
      observerOptions,
    );
    observers[i].observe(document.querySelector(`#${boxID}`));
  }

  // Scroll to the starting position

  document.scrollingElement.scrollTop =
    wrapper.firstElementChild.getBoundingClientRect().top + window.scrollY;
  document.scrollingElement.scrollLeft = 750;
};

intersectionCallback = (entries) => {
  entries.forEach((entry) => {
    const box = entry.target;
    const visiblePct = `${Math.floor(entry.intersectionRatio * 100)}%`;

    box.querySelector(".topLeft").textContent = visiblePct;
    box.querySelector(".topRight").textContent = visiblePct;
    box.querySelector(".bottomLeft").textContent = visiblePct;
    box.querySelector(".bottomRight").textContent = visiblePct;
  });
};

startup();
```

{{EmbedLiveSample("Thresholds", 500, 500)}}

#### ردیابی دید و تأخیر

به طور پیش‌فرض، observer زمانی که عنصر هدف به viewport عنصر ریشه اسکرول می‌شود، اعلان‌هایی ارائه می‌دهد. در حالی که این برای بسیاری از موقعیت‌ها کافی است، گاهی اوقات مهم است که تقاطع‌ها زمانی گزارش نشوند که هدف "از نظر بصری به خطر افتاده" است. به عنوان مثال، هنگام اندازه‌گیری تحلیل‌ها یا impressions تبلیغات، مهم است که عناصر هدف پنهان یا تحریف نشده باشند، به طور کلی یا جزئی.

تنظیم `trackVisibility` به observer می‌گوید که فقط تقاطع‌هایی را برای اهدافی گزارش کند که مرورگر آن‌ها را از نظر بصری به خطر افتاده نمی‌داند، مانند تغییر opacity یا اعمال فیلتر یا transform. الگوریتم محافظه‌کارانه است و ممکن است عناصری را که از نظر فنی قابل مشاهده هستند، مانند آن‌هایی که فقط کاهش جزئی opacity دارند، حذف کند.

محاسبه دید از نظر محاسباتی پرهزینه است و فقط در صورت لزوم باید استفاده شود. هنگام ردیابی دید، باید {{domxref("IntersectionObserver/delay","delay")}} نیز برای محدود کردن حداقل دوره گزارش تنظیم شود. توصیه می‌شود که تأخیر را روی بزرگترین مقدار قابل تحمل تنظیم کنید (حداقل تأخیر هنگام ردیابی دید 100 میلی‌ثانیه است).

#### برش (Clipping) و مستطیل تقاطع

مرورگر مستطیل تقاطع نهایی را به صورت زیر محاسبه می‌کند؛ این کار به طور کامل برای شما انجام می‌شود، اما درک این مراحل می‌تواند برای درک بهتر زمان وقوع تقاطع‌ها مفید باشد.

1. مستطیل محدودکننده عنصر هدف (یعنی کوچک‌ترین مستطیلی که جعبه‌های محدودکننده هر جزء تشکیل‌دهنده عنصر را کاملاً در بر می‌گیرد) با فراخوانی {{domxref("Element.getBoundingClientRect", "getBoundingClientRect()")}} روی هدف به دست می‌آید. این بزرگترین مقداری است که مستطیل تقاطع می‌تواند داشته باشد. مراحل باقی‌مانده هر بخشی را که تقاطع ندارد حذف می‌کنند.
2. با شروع از بلوک والد بلافصل هدف و حرکت به سمت بیرون، برش هر بلوک حاوی (در صورت وجود) روی مستطیل تقاطع اعمال می‌شود. برش یک بلوک بر اساس تقاطع دو بلوک و حالت برش (در صورت وجود) مشخص شده توسط ویژگی {{cssxref("overflow")}} تعیین می‌شود. تنظیم `overflow` بر روی هر چیزی غیر از `visible` باعث برش می‌شود.
3. اگر یکی از عناصر حاوی، ریشه یک context مرور تو در تو (مانند سند موجود در یک {{HTMLElement("iframe")}}) باشد، مستطیل تقاطع به viewport آن context حاوی برش داده می‌شود، و بازگشت به سمت بالا از طریق containerها با بلوک حاوی container ادامه می‌یابد. بنابراین اگر به سطح بالای یک `<iframe>` برسیم، مستطیل تقاطع به viewport فریم برش داده می‌شود، سپس عنصر والد فریم بلوک بعدی است که به سمت ریشه تقاطع بازگشت می‌یابد.
4. هنگامی که بازگشت به سمت بالا به ریشه تقاطع می‌رسد، مستطیل حاصل به فضای مختصات ریشه تقاطع نگاشت می‌شود.
5. سپس مستطیل حاصل با [مستطیل تقاطع ریشه](#the_intersection_root_and_root_margin) به‌روزرسانی می‌شود.
6. در نهایت، این مستطیل به فضای مختصات {{domxref("document")}} هدف نگاشت می‌شود.

## رابط‌ها (Interfaces)

- {{domxref("IntersectionObserver")}}
  - : رابط اصلی برای API Intersection Observer. روش‌هایی برای ایجاد و مدیریت یک observer که می‌تواند هر تعداد عنصر هدف را برای همان پیکربندی تقاطع مشاهده کند، فراهم می‌کند. هر observer می‌تواند به صورت ناهمگام تغییرات در تقاطع بین یک یا چند عنصر هدف و یک عنصر ancestor مشترک یا با {{domxref("Document")}} سطح بالای آن‌ها ({{Glossary('viewport')}}) را مشاهده کند. ancestor یا viewport به عنوان **ریشه (root)** نامیده می‌شود.
- {{domxref("IntersectionObserverEntry")}}
  - : تقاطع بین عنصر هدف و container ریشه آن را در یک لحظه خاص از انتقال توصیف می‌کند. اشیاء از این نوع را فقط می‌توان به دو روش به دست آورد: به عنوان ورودی به callback `IntersectionObserver` شما، یا با فراخوانی {{domxref("IntersectionObserver.takeRecords()")}}.

## یک مثال ساده

این مثال ساده باعث می‌شود یک عنصر هدف با بیشتر یا کمتر قابل مشاهده شدن، رنگ و شفافیت خود را تغییر دهد. در [زمان‌بندی دید عناصر با API Intersection Observer](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility) می‌توانید یک مثال گسترده‌تر پیدا کنید که نحوه زمان‌بندی مدت زمان دید مجموعه‌ای از عناصر (مانند تبلیغات) برای کاربر و واکنش به آن اطلاعات با ثبت آمار یا به‌روزرسانی عناصر را نشان می‌دهد.

### HTML

HTML این مثال بسیار کوتاه است، با یک عنصر اصلی که جعبه مورد نظر ما است (با ID `"box"`) و برخی محتویات درون جعبه.

```html
<div id="box">
  <div class="vertical">Welcome to <strong>The Box!</strong></div>
</div>
```

### CSS

CSS برای اهداف این مثال چندان مهم نیست؛ عنصر را چیدمان می‌کند و مشخص می‌کند که ویژگی‌های {{cssxref("background-color")}} و {{cssxref("border")}} می‌توانند در [انتقال‌های CSS (CSS transitions)](/en-US/docs/Web/CSS/Guides/Transitions) شرکت کنند، که از آن‌ها برای اعمال تغییرات روی عنصر در حین بیشتر یا کمتر مخفی شدن استفاده خواهیم کرد.

```css
#box {
  background-color: rgb(40 40 190 / 100%);
  border: 4px solid rgb(20 20 120);
  transition:
    background-color 1s,
    border 1s;
  width: 350px;
  height: 350px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.vertical {
  color: white;
  font: 32px "Arial";
}

.extra {
  width: 350px;
  height: 350px;
  margin-top: 10px;
  border: 4px solid rgb(20 20 120);
  text-align: center;
  padding: 20px;
}
```

### JavaScript

در نهایت، بیایید نگاهی به کد جاوااسکریپت بیندازیم که از API Intersection Observer برای انجام کارها استفاده می‌کند.

#### تنظیم

ابتدا باید برخی متغیرها را آماده کرده و observer را نصب کنیم.

```js
const numSteps = 20.0;

const boxElement = document.querySelector("#box");
let prevRatio = 0.0;
let increasingColor = "rgb(40 40 190 / ratio)";
let decreasingColor = "rgb(190 40 40 / ratio)";

createObserver();
```

ثابت‌ها و متغیرهایی که در اینجا تنظیم می‌کنیم عبارتند از:

- `numSteps`
  - : یک ثابت که نشان می‌دهد چند threshold می‌خواهیم بین نسبت دید 0.0 و 1.0 داشته باشیم.
- `prevRatio`
  - : این متغیر برای ثبت اینکه آخرین بار که از یک threshold عبور کردیم نسبت دید چقدر بود استفاده می‌شود؛ این به ما امکان می‌دهد بفهمیم که آیا عنصر هدف در حال بیشتر قابل مشاهده شدن است یا کمتر.
- `increasingColor`
  - : یک رشته که رنگی را تعریف می‌کند که وقتی نسبت دید در حال افزایش است به عنصر هدف اعمال می‌کنیم. کلمه "ratio" در این رشته با نسبت دید فعلی هدف جایگزین می‌شود، به طوری که عنصر نه تنها تغییر رنگ می‌دهد، بلکه با کمتر مخفی شدن، opacity آن نیز افزایش می‌یابد.
- `decreasingColor`
  - : به طور مشابه، این یک رشته است که رنگی را تعریف می‌کند که وقتی نسبت دید در حال کاهش است اعمال می‌کنیم.

یک مرجع به عنصر با ID `"box"` با استفاده از {{domxref("Document.querySelector", "querySelector()")}} می‌گیریم، سپس متد `createObserver()` را که در یک لحظه برای مدیریت ساخت و نصب observer تقاطع ایجاد می‌کنیم فراخوانی می‌کنیم.

#### ایجاد observer تقاطع

متد `createObserver()` یک بار پس از بارگذاری کامل صفحه برای ایجاد {{domxref("IntersectionObserver")}} جدید و شروع فرآیند مشاهده عنصر هدف فراخوانی می‌شود.

```js
function createObserver() {
  const options = {
    root: null,
    rootMargin: "0px",
    threshold: buildThresholdList(),
  };

  const observer = new IntersectionObserver(handleIntersect, options);
  observer.observe(boxElement);
}
```

این کار با تنظیم یک شی `options` حاوی تنظیمات observer شروع می‌شود. ما می‌خواهیم تغییرات دید عنصر هدف را نسبت به viewport سند مشاهده کنیم، بنابراین `root` برابر `null` است. به حاشیه نیاز نداریم، بنابراین offset حاشیه، `rootMargin`، به صورت `"0px"` مشخص شده است. این باعث می‌شود observer تغییرات در تقاطع بین مرزهای عنصر هدف و مرزهای viewport را بدون هیچ فضای اضافه شده (یا کم شده) مشاهده کند.

لیست thresholdهای نسبت دید، `threshold`، توسط تابع `buildThresholdList()` ساخته می‌شود. لیست threshold در این مثال به صورت برنامه‌ریزی شده ساخته می‌شود زیرا تعداد زیادی از آن‌ها وجود دارد و تعداد آن قابل تنظیم است.

پس از آماده شدن `options`، observer جدید را ایجاد می‌کنیم، سازنده {{domxref("IntersectionObserver.IntersectionObserver", "IntersectionObserver()")}} را فراخوانی می‌کنیم، یک تابع برای فراخوانی در هنگام عبور تقاطع از یکی از thresholdهای ما مشخص می‌کنیم، `handleIntersect()`، و مجموعه گزینه‌های خود را. سپس {{domxref("IntersectionObserver.observe", "observe()")}} را روی observer بازگردانده شده فراخوانی می‌کنیم و عنصر هدف مورد نظر را به آن ارسال می‌کنیم.

اگر بخواهیم، می‌توانیم چندین عنصر را برای تغییرات تقاطع دید نسبت به viewport با فراخوانی `observer.observe()` برای هر یک از آن عناصر نظارت کنیم.

#### ساخت آرایه نسبت‌های threshold

تابع `buildThresholdList()` که لیست thresholdها را می‌سازد، به این شکل است:

```js
function buildThresholdList() {
  const thresholds = [];
  const numSteps = 20;

  for (let i = 1.0; i <= numSteps; i++) {
    const ratio = i / numSteps;
    thresholds.push(ratio);
  }

  thresholds.push(0);
  return thresholds;
}
```

این آرایه thresholdها را می‌سازد – که هر کدام نسبتی بین 0.0 و 1.0 هستند – با قرار دادن مقدار `i/numSteps` در آرایه `thresholds` برای هر عدد صحیح `i` بین 1 و `numSteps`. همچنین 0 را نیز برای شامل شدن آن مقدار اضافه می‌کند. نتیجه، با توجه به مقدار پیش‌فرض `numSteps` (20)، لیست thresholdهای زیر است:

<table class="standard-table">
    <thead>
      <tr>
        <th>#</th>
        <th>نسبت</th>
        <th>#</th>
        <th>نسبت</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>0</th>
        <td>0.05</td>
        <th>11</th>
        <td>0.6</td>
      </tr>
      <tr>
        <th>1</th>
        <td>0.1</td>
        <th>12</th>
        <td>0.65</td>
      </tr>
      <tr>
        <th>2</th>
        <td>0.15</td>
        <th>13</th>
        <td>0.7</td>
      </tr>
      <tr>
        <th>3</th>
        <td>0.2</td>
        <th>14</th>
        <td>0.75</td>
      </tr>
      <tr>
        <th>4</th>
        <td>0.25</td>
        <th>15</th>
        <td>0.8</td>
      </tr>
      <tr>
        <th>5</th>
        <td>0.3</td>
        <th>16</th>
        <td>0.85</td>
      </tr>
      <tr>
        <th>6</th>
        <td>0.35</td>
        <th>17</th>
        <td>0.9</td>
      </tr>
      <tr>
        <th>7</th>
        <td>0.4</td>
        <th>18</th>
        <td>0.95</td>
      </tr>
      <tr>
        <th>8</th>
        <td>0.45</td>
        <th>19</th>
        <td>1</td>
      </tr>
      <tr>
        <th>9</th>
        <td>0.5</td>
        <th>20</th>
        <td>0</td>
      </tr>
      <tr>
        <th>10</th>
        <td>0.55</td>
      </tr>
    </tbody>
</table>

البته می‌توانستیم آرایه thresholdها را در کد خود به صورت سخت‌کد شده قرار دهیم، و اغلب این کاری است که در نهایت انجام می‌دهید. اما این مثال فضایی برای اضافه کردن کنترل‌های پیکربندی برای تنظیم دانه‌بندی (granularity) باقی می‌گذارد.

#### مدیریت تغییرات تقاطع

هنگامی که مرورگر تشخیص می‌دهد که عنصر هدف (در مورد ما، عنصری با ID `"box"`) نمایان یا مخفی شده است به گونه‌ای که نسبت دید آن از یکی از thresholdهای موجود در لیست ما عبور می‌کند، تابع handler ما، `handleIntersect()` را فراخوانی می‌کند:

```js
function handleIntersect(entries, observer) {
  entries.forEach((entry) => {
    if (entry.intersectionRatio > prevRatio) {
      entry.target.style.backgroundColor = increasingColor.replace(
        "ratio",
        entry.intersectionRatio,
      );
    } else {
      entry.target.style.backgroundColor = decreasingColor.replace(
        "ratio",
        entry.intersectionRatio,
      );
    }

    prevRatio = entry.intersectionRatio;
  });
}
```

برای هر {{domxref("IntersectionObserverEntry")}} در لیست `entries`، نگاه می‌کنیم که آیا {{domxref("IntersectionObserverEntry.intersectionRatio", "intersectionRatio")}} ورودی در حال افزایش است یا خیر؛ اگر هست، {{cssxref("background-color")}} هدف را روی رشته در `increasingColor` تنظیم می‌کنیم (به یاد داشته باشید، این `"rgb(40 40 190 / ratio)"` است)، و کلمه "ratio" را با `intersectionRatio` ورودی جایگزین می‌کند. نتیجه: نه تنها رنگ تغییر می‌کند، بلکه شفافیت عنصر هدف نیز تغییر می‌کند؛ با کاهش نسبت تقاطع، مقدار alpha رنگ پس‌زمینه نیز کاهش می‌یابد و در نتیجه عنصر شفاف‌تری ایجاد می‌شود.

به طور مشابه، اگر `intersectionRatio` در حال کاهش باشد، از رشته `decreasingColor` استفاده می‌کنیم و کلمه "ratio" را در آن با `intersectionRatio` قبل از تنظیم `background-color` عنصر هدف جایگزین می‌کنیم.

در نهایت، برای ردیابی اینکه آیا نسبت تقاطع در حال افزایش یا کاهش است، نسبت فعلی را در متغیر `prevRatio` به خاطر می‌سپاریم.

### نتیجه

در زیر محتوای حاصل آمده است. این صفحه را بالا و پایین اسکرول کنید و توجه کنید که ظاهر جعبه با انجام این کار چگونه تغییر می‌کند.

{{EmbedLiveSample('A_simple_example', 400, 400)}}

یک مثال حتی گسترده‌تر در [زمان‌بندی دید عناصر با API Intersection Observer](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility) وجود دارد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Polyfill Intersection Observer](https://github.com/w3c/IntersectionObserver)
- [زمان‌بندی دید عناصر با API Intersection Observer](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility)
- {{domxref("IntersectionObserver")}} و {{domxref("IntersectionObserverEntry")}}