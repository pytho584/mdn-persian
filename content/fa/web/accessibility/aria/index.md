---
title: "ARIA"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA"
translated_by: "n8n + AI"
---

---
title: ARIA
slug: Web/Accessibility/ARIA
page-type: landing-page
sidebar: accessibilitysidebar
---

برنامه‌های غنی اینترنتی دسترس‌پذیر **(<abbr>ARIA</abbr>)** مجموعه‌ای از [نقش‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) و [ویژگی‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes) است که روش‌هایی را برای قابل‌دسترس‌تر کردن محتوای وب و برنامه‌های وب (به‌ویژه آن‌هایی که با جاوااسکریپت توسعه یافته‌اند) برای افراد دارای معلولیت تعریف می‌کند.

ARIA مکمل HTML است تا تعاملات و ویجت‌هایی که معمولاً در برنامه‌ها استفاده می‌شوند، زمانی که مکانیزم دیگری وجود ندارد، به فناوری‌های کمکی منتقل شوند. برای مثال، ARIA ویجت‌های جاوااسکریپتی قابل‌دسترس، راهنمایی‌ها و پیام‌های خطای فرم، به‌روزرسانی‌های زنده محتوا و موارد دیگر را ممکن می‌سازد.

## قبل از استفاده از ARIA

> [!WARNING]
> بسیاری از این ویجت‌ها در مرورگرهای مدرن به‌طور کامل پشتیبانی می‌شوند. **توسعه‌دهندگان باید ترجیح دهند از عنصر HTML معنایی صحیح به جای ARIA استفاده کنند**، اگر چنین عنصری وجود داشته باشد. به‌عنوان مثال، عناصر بومی دارای [دسترس‌پذیری صفحه‌کلید](/en-US/docs/Web/Accessibility/Guides/Keyboard-navigable_JavaScript_widgets)، نقش‌ها و حالت‌های داخلی هستند. با این حال، اگر تصمیم به استفاده از ARIA دارید، شما مسئول شبیه‌سازی رفتار معادل مرورگر در اسکریپت هستید.

> [اولین قانون ARIA](https://w3c.github.io/using-aria/#rule1) این است: «اگر می‌توانید از یک عنصر یا ویژگی HTML بومی استفاده کنید که معناشناسی و رفتاری که نیاز دارید از قبل در آن تعبیه شده است، به جای تغییر کاربری یک عنصر و افزودن نقش، حالت یا ویژگی ARIA برای قابل‌دسترس کردن آن، این کار را انجام دهید.»

> [!NOTE]
> ضرب‌المثلی وجود دارد: «نبود ARIA بهتر از ARIA بد است.» در [بررسی WebAim از بیش از یک میلیون صفحه اصلی](https://webaim.org/projects/million/#aria)، آن‌ها دریافتند که صفحات اصلی دارای ARIA به‌طور میانگین ۴۱٪ خطاهای شناسایی‌شده بیشتری نسبت به صفحات بدون ARIA دارند. در حالی که ARIA برای قابل‌دسترس کردن صفحات وب طراحی شده است، اگر به‌درستی استفاده نشود، می‌تواند بیشتر از اینکه مفید باشد ضرر برساند.

در ادامه، نشانه‌گذاری یک ویجت نوار پیشرفت آمده است:

```html
<div
  id="percent-loaded"
  role="progressbar"
  aria-valuenow="75"
  aria-valuemin="0"
  aria-valuemax="100"></div>
```

این نوار پیشرفت با استفاده از یک {{HTMLElement("div")}} ساخته شده است که معنایی ندارد. ما نقش‌ها و ویژگی‌های ARIA را برای افزودن معنا اضافه می‌کنیم. در این مثال، ویژگی [`role="progressbar"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role) به مرورگر اطلاع می‌دهد که این عنصر در واقع یک ویجت نوار پیشرفت مبتنی بر جاوااسکریپت است. ویژگی‌های [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) و [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) حداقل و حداکثر مقادیر نوار پیشرفت را مشخص می‌کنند و [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) وضعیت فعلی آن را توصیف می‌کند و بنابراین باید با جاوااسکریپت به‌روز نگه داشته شود.

علاوه بر قرار دادن مستقیم آن‌ها در نشانه‌گذاری، ویژگی‌های ARIA را می‌توان با استفاده از کد جاوااسکریپت به عنصر اضافه کرد و به‌صورت پویا به‌روزرسانی کرد، مانند این:

```js
// Find the progress bar <div> in the DOM.
const progressBar = document.getElementById("percent-loaded");

// Set its ARIA roles and states,
// so that assistive technologies know what kind of widget it is.
progressBar.setAttribute("role", "progressbar");
progressBar.setAttribute("aria-valuemin", 0);
progressBar.setAttribute("aria-valuemax", 100);

// Create a function that can be called at any time to update
// the value of the progress bar.
function updateProgress(percentComplete) {
  progressBar.setAttribute("aria-valuenow", percentComplete);
}
```

تمام محتوایی که برای کاربران غیر فناوری کمکی در دسترس است، باید برای فناوری‌های کمکی نیز در دسترس قرار گیرد. به همین ترتیب، نباید هیچ ویژگی‌ای گنجانده شود که فقط برای کاربران فناوری کمکی باشد و برای افرادی که از فناوری کمکی استفاده نمی‌کنند نیز قابل‌دسترس نباشد. نوار پیشرفت بالا باید استایل‌دهی شود تا شبیه یک نوار پیشرفت به نظر برسد.

در عوض استفاده از عنصر بومی {{HTMLElement('progress')}} بسیار ساده‌تر بود:

```html
<progress id="percent-loaded" value="75" max="100">75 %</progress>
```

> [!NOTE]
> ویژگی `min` برای عنصر {{HTMLElement('progress')}} مجاز نیست؛ مقدار حداقل آن همیشه `0` است.

> [!NOTE]
> عناصر ساختاری HTML ({{HTMLElement("main")}}، {{HTMLElement("header")}}، {{HTMLElement("nav")}} و غیره) دارای نقش‌های ARIA ضمنی داخلی هستند، بنابراین نیازی به تکرار آن‌ها نیست.

## پشتیبانی

مانند هر فناوری وب دیگری، درجات مختلفی از پشتیبانی برای ARIA وجود دارد. پشتیبانی بر اساس سیستم‌عامل و مرورگر مورد استفاده و همچنین نوع فناوری کمکی که با آن ارتباط برقرار می‌کند، متفاوت است. علاوه بر این، نسخه سیستم‌عامل، مرورگر و فناوری کمکی عوامل مؤثری هستند. نسخه‌های قدیمی‌تر نرم‌افزار ممکن است از برخی نقش‌های ARIA پشتیبانی نکنند، فقط پشتیبانی جزئی داشته باشند یا عملکرد آن را به‌درستی گزارش نکنند.

همچنین مهم است که اذعان کنیم برخی از افرادی که به فناوری کمکی وابسته هستند، از ترس از دست دادن توانایی تعامل با رایانه و مرورگر خود، تمایلی به ارتقای نرم‌افزار خود ندارند. به همین دلیل، مهم است که در صورت امکان از [عناصر HTML معنایی](/en-US/docs/Learn_web_development/Core/Accessibility/HTML) استفاده کنید، زیرا HTML معنایی پشتیبانی بسیار بهتری از فناوری کمکی دارد.

همچنین مهم است که ARIA نوشته‌شده خود را با فناوری کمکی واقعی آزمایش کنید.这是因为 شبیه‌سازهای مرورگر و شبیه‌سازها واقعاً برای آزمایش پشتیبانی کامل مؤثر نیستند. به‌طور مشابه، راه‌حل‌های پروکسی فناوری کمکی برای تضمین کامل عملکرد کافی نیستند.

## مرجع

[مرجع ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference) فهرست جامعی از ویژگی‌ها و نقش‌های ARIA است که در MDN مستند شده‌اند.

- [نقش‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles)
  - : نقش‌های ARIA می‌توانند برای توصیف عناصری استفاده شوند که به‌طور بومی در HTML وجود ندارند یا عناصری که وجود دارند اما هنوز پشتیبانی گسترده‌ای در مرورگر ندارند.
- [حالت‌ها و ویژگی‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes)
  - : ویژگی‌های ARIA امکان تغییر حالت‌ها و ویژگی‌های یک عنصر را مطابق تعریف در درخت دسترس‌پذیری فراهم می‌کنند.

## راهنماها

[راهنماهای ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides) منابعی هستند که به شما کمک می‌کنند دسترس‌پذیری ویژگی‌های صفحات وب مانند جدول‌ها، فرم‌ها و ناوبری با صفحه‌کلید را بهبود بخشید.

## تلاش‌های استانداردسازی

- [مشخصات WAI-ARIA](https://w3c.github.io/aria/)
  - : خود مشخصات W3C.
- [روش‌های تألیف WAI-ARIA](https://www.w3.org/WAI/ARIA/apg/)
  - : اسناد رسمی بهترین شیوه‌ها نحوه بهترین کاربرد ARIA برای ویجت‌ها و تعاملات رایج را شرح می‌دهند. منبعی عالی.

## ARIA برای ویجت‌های اسکریپت‌شده

- [نوشتن ویجت‌های جاوااسکریپتی قابل‌ناوبری با صفحه‌کلید](/en-US/docs/Web/Accessibility/Guides/Keyboard-navigable_JavaScript_widgets)
  - : عناصر داخلی مانند {{HTMLElement("input")}}، {{HTMLElement("button")}} و غیره دارای دسترس‌پذیری داخلی صفحه‌کلید هستند. اگر این‌ها را با {{HTMLElement("div")}} و ARIA شبیه‌سازی کنید، باید اطمینان حاصل کنید که ویجت‌های شما قابل‌ناوبری با صفحه‌کلید هستند.
- [مناطق زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)
  - : مناطق زنده پیشنهادهایی به صفحه‌خوان‌ها ارائه می‌دهند درباره نحوه مدیریت تغییرات محتوای یک صفحه.

## ویدئوها

سخنرانی‌های زیر راهی عالی برای درک ARIA هستند:

[ARIA، APIهای دسترس‌پذیری و کدنویسی طوری که انگار واقعاً اهمیت می‌دهی! – لئونی واتسون](https://www.youtube.com/watch?v=qdB8SRhqvFc)