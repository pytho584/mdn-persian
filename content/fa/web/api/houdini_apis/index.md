---
title: Houdini APIs
slug: Web/API/Houdini_APIs
page-type: guide
---

{{DefaultAPISidebar("Houdini API")}}

Houdini مجموعه‌ای از APIهای سطح پایین است که بخش‌هایی از موتور CSS را نمایان می‌کند و به توسعه‌دهندگان قدرت می‌دهد تا با اتصال به فرایند استایل‌دهی و چیدمان موتور رندر مرورگر، CSS را گسترش دهند. Houdini گروهی از APIهاست که دسترسی مستقیم به [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) (CSSOM) را فراهم می‌کند و توسعه‌دهندگان را قادر می‌سازد کدی بنویسند که مرورگر بتواند آن را به‌عنوان CSS تجزیه کند، بدین ترتیب ویژگی‌های جدید CSS را بدون انتظار برای پیاده‌سازی بومی آن‌ها در مرورگرها ایجاد کنند.

## مزایای Houdini

Houdini زمان تجزیه سریع‌تری نسبت به استفاده از JavaScript {{domxref("HTMLElement.style")}} برای تغییرات استایل فراهم می‌کند. مرورگرها CSSOM — شامل فرایندهای چیدمان، نقاشی و ترکیب — را قبل از اعمال هرگونه به‌روزرسانی استایل موجود در اسکریپت‌ها تجزیه می‌کنند. علاوه بر این، فرایندهای چیدمان، نقاشی و ترکیب برای به‌روزرسانی‌های استایل جاوااسکریپتی تکرار می‌شوند. کد Houdini منتظر تکمیل چرخه رندر اول نمی‌ماند. بلکه در همان چرخه اول گنجانده می‌شود — استایل‌های قابل رندر و قابل فهم ایجاد می‌کند. Houdini یک API مبتنی بر شیء برای کار با مقادیر CSS در جاوااسکریپت فراهم می‌کند.

[API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Typed_OM_API) (CSS Typed Object Model API) یک مدل شیء CSS با انواع و متدهاست که مقادیر را به‌عنوان اشیاء جاوااسکریپتی نمایان می‌کند و دستکاری شهودی‌تری نسبت به دستکاری‌های قبلی مبتنی بر رشته {{domxref("HTMLElement.style")}} فراهم می‌کند. هر عنصر و قانون استایل‌شیت دارای یک نقشه استایل است که از طریق {{domxref("StylePropertyMap")}} آن قابل دسترسی است.

یکی از ویژگی‌های CSS Houdini {{domxref("Worklet")}} است. با ورکلت‌ها می‌توانید CSS مدولار ایجاد کنید که تنها با یک خط کد جاوااسکریپت برای وارد کردن کامپوننت‌های قابل پیکربندی نیاز دارد: بدون نیاز به پیش‌پردازنده، پس‌پردازنده یا فریم‌ورک جاوااسکریپت.

```js
CSS.paintWorklet.addModule("css-component.js");
```

این ماژول اضافه‌شده شامل توابع {{domxref("PaintWorkletGlobalScope.registerPaint")}} است که ورکلت‌های کاملاً قابل پیکربندی را ثبت می‌کنند.

تابع `paint()` CSS یک تابع اضافی است که توسط نوع {{cssxref("image")}} پشتیبانی می‌شود. این تابع پارامترهایی شامل نام ورکلت و همچنین پارامترهای اضافی مورد نیاز ورکلت را می‌گیرد. ورکلت همچنین به ویژگی‌های سفارشی عنصر دسترسی دارد: نیازی به ارسال آن‌ها به‌عنوان آرگومان تابع نیست.

در مثال زیر تابع `paint()` یک ورکلت به نام `my-component` را دریافت می‌کند.

```css
li {
  background-image: paint(my-component, stroke, 10px);
  --highlights: blue;
  --theme: green;
}
```

> [!NOTE]
> با قدرت زیاد، مسئولیت زیادی نیز همراه است! با Houdini می‌توانید پیاده‌سازی مخصوص خود را برای masonry، grid یا regions ابداع کنید، اما انجام این کار لزوماً بهترین ایده نیست. گروه کاری CSS کار زیادی برای اطمینان از عملکرد، مدیریت تمام موارد لبه، و در نظر گرفتن امنیت، حریم شخصی و دسترسی‌پذیری انجام می‌دهد. هنگام گسترش CSS با Houdini، حتماً این ملاحظات را در نظر داشته باشید و قبل از حرکت به پروژه‌های بلندپروازانه‌تر، با پروژه‌های کوچک شروع کنید.

## APIهای Houdini

در زیر می‌توانید پیوندهایی به صفحات مرجع اصلی پوشش‌دهنده APIهایی که در چتر Houdini قرار می‌گیرند، همراه با پیوندهایی به راهنماهایی که در یادگیری نحوه استفاده از آن‌ها کمک می‌کنند، پیدا کنید.

### API ویژگی‌ها و مقادیر CSS (CSS Properties and Values API)

APIای برای ثبت ویژگی‌های جدید CSS تعریف می‌کند. ویژگی‌های ثبت‌شده با استفاده از این API دارای یک نحو تجزیه هستند که یک نوع، رفتار وراثت و یک مقدار اولیه را تعریف می‌کند.

- [مرجع API ویژگی‌ها و مقادیر CSS](/en-US/docs/Web/API/CSS_Properties_and_Values_API)
- [راهنمای API ویژگی‌ها و مقادیر CSS](/en-US/docs/Web/API/CSS_Properties_and_Values_API/guide)
- [Smarter custom properties with Houdini's new API](https://web.dev/articles/css-props-and-vals)

### CSS Typed OM

تبدیل رشته‌های مقدار CSSOM به نمایش‌های جاوااسکریپتی تایپ‌شده و بالعکس می‌تواند هزینه عملکرد قابل توجهی داشته باشد. CSS Typed OM مقادیر CSS را به‌عنوان اشیاء جاوااسکریپتی تایپ‌شده نمایان می‌کند تا امکان دستکاری کارآمد آن‌ها فراهم شود.

- [مرجع CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API)
- [راهنمای CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [Working with the new CSS Typed Object Model](https://developer.chrome.com/docs/css-ui/cssom)

### API نقاشی CSS (CSS Painting API)

API نقاشی که برای بهبود قابلیت گسترش CSS توسعه یافته است، به توسعه‌دهندگان اجازه می‌دهد توابع جاوااسکریپتی بنویسند که می‌توانند مستقیماً روی پس‌زمینه، حاشیه یا محتوای یک عنصر از طریق تابع `paint()` CSS رسم کنند.

- [مرجع API نقاشی CSS](/en-US/docs/Web/API/CSS_Painting_API)
- [راهنمای API نقاشی CSS](/en-US/docs/Web/API/CSS_Painting_API/Guide)
- [CSS Paint API](https://developer.chrome.com/blog/paintapi/)
- [The CSS Paint API](https://css-tricks.com/the-css-paint-api/)
- [Simulating Drop Shadows with the CSS Paint API](https://css-tricks.com/simulating-drop-shadows-with-the-css-paint-api/)
- [CSS Paint API Being predictably random](https://jakearchibald.com/2020/css-paint-predictably-random/)

### Worklets

APIای برای اجرای اسکریپت‌ها در مراحل مختلف خط لوله رندرگیری مستقل از محیط اصلی اجرای جاوااسکریپت. Worklets از نظر مفهومی مشابه [Web Workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers) هستند و توسط موتور رندر فراخوانی شده و آن را گسترش می‌دهند.

- [مرجع Worklets](/en-US/docs/Web/API/Worklet)

### API چیدمان CSS (CSS Layout API)

این API که برای بهبود قابلیت گسترش CSS طراحی شده است، توسعه‌دهندگان را قادر می‌سازد الگوریتم‌های چیدمان خود را بنویسند، مانند masonry یا line snapping.

_این API تا حدی در Chrome Canary پشتیبانی می‌شود. هنوز در MDN مستند نشده است._

### API تجزیه‌گر CSS (CSS Parser API)

APIای که تجزیه‌گر CSS را مستقیم‌تر نمایان می‌کند، برای تجزیه زبان‌های شبه CSS دلخواه به یک نمایش با تایپ ضعیف.

_این API در حال حاضر یک پیشنهاد است و پیاده‌سازی مرورگری یا مستندی در MDN ندارد._

- [پیشنهاد](https://github.com/WICG/css-parser-api)

### API معیارهای فونت (Font Metrics API)

APIای که معیارهای فونت را نمایان می‌کند و دسترسی به نتایج چیدمان تایپوگرافی را فراهم می‌کند.

_این API در حال حاضر یک پیشنهاد است و پیاده‌سازی مرورگری یا مستندی در MDN ندارد._

- [پیشنهاد](https://github.com/w3c/css-houdini-drafts/blob/main/font-metrics-api/README.md)

## همچنین ببینید

- [A Practical Overview of CSS Houdini](https://www.smashingmagazine.com/2020/03/practical-overview-css-houdini/)
- [Smarter custom properties with Houdini's new API](https://web.dev/articles/css-props-and-vals)