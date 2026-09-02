---
title: "MediaQueryList"
---

---
title: MediaQueryList
slug: Web/API/MediaQueryList
page-type: web-api-interface
browser-compat: api.MediaQueryList
---

{{APIRef("CSSOM view API")}}

یک شیء **`MediaQueryList`** اطلاعات مربوط به یک [media query](/en-US/docs/Web/CSS/Guides/Media_queries) (پرسوجوی رسانهای) اعمال‌شده روی سند را ذخیره می‌کند. این شیء امکان تطبیق با وضعیت سند را هم به‌صورت فوری و هم به‌صورت رویدادمحور فراهم می‌کند.

می‌توانید با فراخواندن {{DOMxRef("Window.matchMedia", "matchMedia()")}} روی شیء {{DOMxRef("window")}} یک `MediaQueryList` بسازید. شیء حاصل، هنگام تغییر وضعیت media query (یعنی زمانی که نتیجهٔ آزمون media query به `true` تبدیل می‌شود یا از `true` خارج می‌شود) اعلان‌هایی به شنوندگان (listeners) ارسال می‌کند.

این قابلیت برای طراحی تطبیقی (adaptive design) بسیار مفید است؛ زیرا به‌جای بررسی دوره‌ای مقادیر، می‌توان سند را زیر نظر گرفت تا تغییر وضعیت media queryها را تشخیص داد و بر اساس وضعیت media query، تغییرات سند را به‌صورت برنامه‌نویسی‌شده اعمال کرد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_رابطِ `MediaQueryList` ویژگی‌های خود را از رابطِ والد، یعنی {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{DOMxRef("MediaQueryList.matches", "matches")}} {{ReadOnlyInline}}
  - : یک مقدار بولی (boolean) که اگر {{DOMxRef("document")}} در حال حاضر با فهرست media query مطابقت داشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.
- {{DOMxRef("MediaQueryList.media", "media")}} {{ReadOnlyInline}}
  - : یک رشته (string) که یک media query سریال‌سازی‌شده را نمایش می‌دهد.

## متدهای نمونه

_رابطِ `MediaQueryList` متدهای خود را از رابطِ والد، یعنی {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{DOMxRef("MediaQueryList.addListener", "addListener()")}} {{deprecated_inline}}
  - : یک تابع callback به `MediaQueryList` اضافه می‌کند که هر زمان وضعیت media query تغییر کند — یعنی هر زمان سند با media queryهای موجود در فهرست مطابقت پیدا کند یا از مطابقت خارج شود — فراخوانی می‌شود. این متد عمدتاً برای سازگاری با نسخه‌های قدیمی‌تر وجود دارد؛ در صورت امکان بهتر است به‌جای آن از {{domxref("EventTarget.addEventListener", "addEventListener()")}} برای شنیدن رویداد {{domxref("MediaQueryList.change_event", "change")}} استفاده کنید.
- {{DOMxRef("MediaQueryList.removeListener", "removeListener()")}} {{deprecated_inline}}
  - : تابع callback شنوندهٔ مشخص‌شده را از مجموعهٔ callbackهایی که هنگام تغییر وضعیت media query در `MediaQueryList` فراخوانی می‌شوند، حذف می‌کند؛ این تغییر هر بار که سند بین مطابقت و عدم مطابقت با media queryهای فهرست‌شده در `MediaQueryList` جابه‌جا شود رخ می‌دهد. این متد برای سازگاری با نسخه‌های قدیمی‌تر حفظ شده است؛ در صورت امکان بهتر است برای حذف callbackهای اعلان تغییر از {{domxref("EventTarget.removeEventListener", "removeEventListener()")}} استفاده کنید (که قبلاً باید با `addEventListener()` اضافه شده باشند).

## رویدادها

_رویدادهای زیر به اشیاء `MediaQueryList` ارسال می‌شوند:_

- {{DOMxRef("MediaQueryList.change_event", "change")}}
  - : هنگامی که نتیجهٔ اجرای media query روی سند تغییر کند، به `MediaQueryList` ارسال می‌شود. برای مثال، اگر media query برابر با `(width >= 400px)` باشد، هر بار که عرض {{Glossary("viewport")}} سند طوری تغییر کند که از مرز 400px در هر یک از دو جهت عبور کند، رویداد `change` رخ می‌دهد.

## مثال‌ها

این مثال یک `MediaQueryList` می‌سازد و سپس یک شنونده تنظیم می‌کند تا تغییر وضعیت media query را تشخیص دهد و هنگام این تغییر، تابعی سفارشی برای تغییر ظاهر صفحه اجرا کند.

```js
const para = document.querySelector("p");
const mql = window.matchMedia("(width <= 600px)");

function screenTest(e) {
  if (e.matches) {
    /* the viewport is 600 pixels wide or less */
    para.textContent = "This is a narrow screen — less than 600px wide.";
    document.body.style.backgroundColor = "red";
  } else {
    /* the viewport is more than 600 pixels wide */
    para.textContent = "This is a wide screen — more than 600px wide.";
    document.body.style.backgroundColor = "blue";
  }
}

mql.addEventListener("change", screenTest);
```

> [!NOTE]
> می‌توانید این مثال را در GitHub پیدا کنید (هم [کد منبع](https://github.com/mdn/dom-examples/blob/main/mediaquerylist/index.html) را ببینید و هم [نسخهٔ در حال اجرا](https://mdn.github.io/dom-examples/mediaquerylist/index.html) را مشاهده کنید).

همچنین می‌توانید مثال‌های دیگری را در صفحهٔ هر یک از ویژگی‌ها و متدها پیدا کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [Using media queries from code](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryListEvent")}}
- مقالهٔ {{DOMxRef("Window.devicePixelRatio")}} نیز یک مثال کاربردی دارد.