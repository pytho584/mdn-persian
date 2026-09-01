---
title: "HTMLScriptElement"
slug: Web/API/HTMLScriptElement
page-type: web-api-interface
browser-compat: api.HTMLScriptElement
---

{{APIRef("HTML DOM")}}

المان‌های HTML {{HTMLElement("script")}}، رابط `HTMLScriptElement` را نمایان می‌کنند که ویژگی‌ها و روش‌های خاصی برای دستکاری رفتار و اجرای المان‌های `<script>` (فراتر از رابط به‌ارث‌بردهٔ {{domxref("HTMLElement")}}) فراهم می‌کند.

فایل‌های جاوااسکریپت باید با [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) به‌صورت `text/javascript` ارائه شوند، اما مرورگرها انعطاف‌پذیر هستند و تنها در صورتی آن‌ها را مسدود می‌کنند که اسکریپت با یک نوع تصویری (`image/*`)، نوع ویدیویی (`video/*`)، نوع صوتی (`audio/*`) یا `text/csv` ارائه شود. اگر اسکریپت مسدود شود، المان آن رویداد {{domxref("HTMLElement/error_event", "error")}} دریافت می‌کند؛ در غیر این صورت، رویداد {{domxref("Window/load_event", "load")}} را دریافت می‌کند.

> [!NOTE]
> وقتی با استفاده از روش {{domxref("Document.write()")}} درج می‌شوند، المان‌های {{HTMLElement("script")}} (معمولاً به‌صورت همزمان) اجرا می‌شوند، اما وقتی با استفاده از {{domxref("Element.innerHTML")}} یا {{domxref("Element.outerHTML")}} درج می‌شوند، اصلاً اجرا نمی‌شوند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLScriptElement.attributionSrc")}} {{securecontext_inline}} {{deprecated_inline}} {{non-standard_inline}}
  - : ویژگی [`attributionsrc`](/en-US/docs/Web/HTML/Reference/Elements/script#attributionsrc) را روی یک المان {{htmlelement("script")}} به‌صورت برنامه‌نویسی‌شده تنظیم و بازیابی می‌کند و مقدار آن ویژگی را منعکس می‌کند. `attributionsrc` مشخص می‌کند که می‌خواهید مرورگر هدر {{httpheader("Attribution-Reporting-Eligible")}} را همراه با درخواست منبع اسکریپت ارسال کند. در سمت سرور، از این برای راه‌اندازی ارسال هدر {{httpheader("Attribution-Reporting-Register-Source")}} یا {{httpheader("Attribution-Reporting-Register-Trigger")}} در پاسخ استفاده می‌شود، به‌ترتیب برای ثبت یک [منبع attribution مبتنی بر جاوااسکریپت](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#javascript-based_event_sources) یا [trigger attribution](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers#javascript-based_attribution_triggers).
- {{domxref("HTMLScriptElement.async")}}
  - : یک مقدار بولی که نحوهٔ اجرای اسکریپت را کنترل می‌کند. برای اسکریپت‌های کلاسیک، اگر ویژگی `async` روی `true` تنظیم شود، اسکریپت خارجی به‌صورت موازی با تجزیهٔ (parsing) سند واکشی می‌شود و به محض در دسترس بودن ارزیابی می‌شود. برای [اسکریپت‌های ماژول](/en-US/docs/Web/JavaScript/Guide/Modules)، اگر ویژگی `async` روی `true` تنظیم شود، اسکریپت و همهٔ وابستگی‌های آن به‌صورت موازی با تجزیه واکشی می‌شوند و به محض در دسترس بودن ارزیابی می‌شوند.
- {{domxref("HTMLScriptElement.blocking")}}
  - : یک رشته که نشان می‌دهد برخی عملیات خاص باید تا زمان واکشی اسکریپت مسدود شوند. این ویژگی، ویژگی `blocking` المان {{HTMLElement("script")}} را منعکس می‌کند.
- `HTMLScriptElement.charset` {{deprecated_inline}}
  - : یک رشته که نشان‌دهندهٔ encoding کاراکتر یک اسکریپت خارجی است. این ویژگی، ویژگی [`charset`](/en-US/docs/Web/HTML/Reference/Elements/script#charset) را منعکس می‌کند.
- {{domxref("HTMLScriptElement.crossOrigin")}}
  - : یک رشته که [تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مربوط به المان اسکریپت را منعکس می‌کند. برای اسکریپت‌های کلاسیک از [originهای](/en-US/docs/Glossary/Origin) دیگر، این ویژگی کنترل می‌کند که آیا اطلاعات خطا در معرض نمایش قرار گیرند یا نه.
- {{domxref("HTMLScriptElement.defer")}}
  - : یک مقدار بولی که نحوهٔ اجرای اسکریپت را کنترل می‌کند. برای اسکریپت‌های کلاسیک، اگر ویژگی `defer` روی `true` تنظیم شود، اسکریپت خارجی پس از تجزیهٔ سند، اما قبل از رویداد {{domxref("Document/DOMContentLoaded_event", "DOMContentLoaded")}} اجرا می‌شود. برای [اسکریپت‌های ماژول](/en-US/docs/Web/JavaScript/Guide/Modules)، ویژگی `defer` هیچ اثری ندارد.
- `HTMLScriptElement.event` {{deprecated_inline}}
  - : یک رشته؛ روشی منسوخ برای ثبت مدیریت‌کننده‌های رویداد روی المان‌ها در یک سند HTML.
- {{domxref("HTMLScriptElement.fetchPriority")}}
  - : یک رشته اختیاری که نشان‌دهندهٔ یک راهنمایی (hint) به مرورگر است دربارهٔ اینکه چگونه باید واکشی یک اسکریپت خارجی را نسبت به سایر اسکریپت‌های خارجی اولویت‌بندی کند. اگر این مقدار ارائه شود، باید یکی از مقادیر مجاز باشد: `high` برای واکشی با اولویت بالا، `low` برای واکشی با اولویت پایین، یا `auto` برای نشان دادن بدون اولویت (که پیش‌فرض است). این ویژگی، ویژگی `fetchpriority` المان {{HTMLElement("script")}} را منعکس می‌کند.
- {{domxref("HTMLScriptElement.innerText")}}
  - : یک ویژگی که محتوای متنی درون‌خطی المان {{HTMLElement("script")}} را طوری نشان می‌دهد که گویی متن رندر شده است. این ویژگی یا یک شیء {{domxref("TrustedScript")}} یا یک رشته را می‌پذیرد.
- {{domxref("HTMLScriptElement.integrity")}}
  - : یک رشته که شامل فرادادهٔ درون‌خطی است که مرورگر می‌تواند از آن برای تأیید اینکه یک منبع واکشی‌شده بدون دستکاری غیرمنتظره تحویل داده شده است استفاده کند. این ویژگی، ویژگی `integrity` المان {{HTMLElement("script")}} را منعکس می‌کند.
- {{domxref("HTMLScriptElement.noModule")}}
  - : یک مقدار بولی که اگر `true` باشد، اجرای اسکریپت را در مرورگرهایی که از [ماژول‌های ES](/en-US/docs/Web/JavaScript/Guide/Modules) پشتیبانی می‌کنند متوقف می‌کند — این ویژگی برای اجرای اسکریپت‌های جایگزین در مرورگرهای قدیمی‌تری استفاده می‌شود که از ماژول‌های جاوااسکریپت پشتیبانی _نمی‌کنند_.
- {{domxref("HTMLScriptElement.referrerPolicy")}}
  - : یک رشته که ویژگی HTML [`referrerPolicy`](/en-US/docs/Web/HTML/Reference/Elements/script#referrerpolicy) را منعکس می‌کند و نشان می‌دهد هنگام واکشی اسکریپت و واکشی‌هایی که توسط آن اسکریپت انجام می‌شود، کدام referrer استفاده شود.
- {{domxref("HTMLScriptElement.src")}}
  - : یک {{domxref("TrustedScriptURL")}} یا رشته که URL یک اسکریپت خارجی را نشان می‌دهد؛ این می‌تواند به عنوان جایگزینی برای جاسازی مستقیم اسکریپت در یک سند استفاده شود. این ویژگی، ویژگی `src` المان {{HTMLElement("script")}} را منعکس می‌کند.
- {{domxref("HTMLScriptElement.text")}}
  - : یک ویژگی که محتوای متنی درون‌خطی المان {{HTMLElement("script")}} را نشان می‌دهد. این ویژگی یا یک شیء {{domxref("TrustedScript")}} یا یک رشته را می‌پذیرد. این ویژگی همانند ویژگی [`textContent`](/en-US/docs/Web/API/HTMLScriptElement/textContent) عمل می‌کند.
- {{domxref("HTMLScriptElement.textContent")}}
  - : یک ویژگی که محتوای متنی درون‌خطی المان {{HTMLElement("script")}} را نشان می‌دهد. این ویژگی از {{domxref("Node/textContent","Node")}} بازتعریف شده است تا از {{domxref("TrustedScript")}} به عنوان ورودی پشتیبانی کند. روی این المان دقیقاً مانند ویژگی [`text`](/en-US/docs/Web/API/HTMLScriptElement/text) رفتار می‌کند.
- {{domxref("HTMLScriptElement.type")}}
  - : یک رشته که نوع اسکریپت را نشان می‌دهد. این ویژگی، ویژگی `type` المان {{HTMLElement("script")}} را منعکس می‌کند.

## روش‌های ایستا

- {{domxref("HTMLScriptElement.supports_static", "HTMLScriptElement.supports()")}}
  - : اگر مرورگر از اسکریپت‌های نوع مشخص‌شده پشتیبانی کند، `true` و در غیر این صورت `false` برمی‌گرداند. این روش یک سازوکار ساده و یکپارچه برای تشخیص ویژگی‌های مربوط به اسکریپت فراهم می‌کند.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## رویدادها

_رویداد خاصی ندارد؛ رویدادهای والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مثال‌ها

### وارد کردن پویای اسکریپت‌ها

بیایید تابعی بسازیم که اسکریپت‌های جدید را در یک سند وارد می‌کند و یک گرهٔ {{HTMLElement("script")}} را _دقیقاً قبل از_ {{HTMLElement("script")}} که کد زیر را میزبانی می‌کند (از طریق {{domxref("document.currentScript")}}) ایجاد می‌کند. این اسکریپت‌ها به‌صورت **ناهمگام** اجرا خواهند شد. برای جزئیات بیشتر، ویژگی‌های [`defer`](/en-US/docs/Web/API/HTMLScriptElement/defer) و [`async`](/en-US/docs/Web/API/HTMLScriptElement/async) را ببینید.

```js
function loadError(oError) {
  throw new URIError(`The script ${oError.target.src} didn't load correctly.`);
}

function prefixScript(url, onloadFunction) {
  const newScript = document.createElement("script");
  newScript.onerror = loadError;
  if (onloadFunction) {
    newScript.onload = onloadFunction;
  }
  document.currentScript.parentNode.insertBefore(
    newScript,
    document.currentScript,
  );
  newScript.src = url;
}
```

تابع بعدی، به جای قرار دادن اسکریپت‌های جدید بلافاصله قبل از المان {{domxref("document.currentScript")}}، آن‌ها را به عنوان فرزندان تگ {{HTMLElement("head")}} اضافه می‌کند.

```js
function loadError(oError) {
  throw new URIError(`The script ${oError.target.src} didn't load correctly.`);
}

function affixScriptToHead(url, onloadFunction) {
  const newScript = document.createElement("script");
  newScript.onerror = loadError;
  if (onloadFunction) {
    newScript.onload = onloadFunction;
  }
  document.head.appendChild(newScript);
  newScript.src = url;
}
```

نمونهٔ استفاده:

```js
affixScriptToHead("myScript1.js");
affixScriptToHead("myScript2.js", () => {
  alert('The script "myScript2.js" has been correctly loaded.');
});
```

### بررسی اینکه آیا یک نوع اسکریپت پشتیبانی می‌شود

{{domxref("HTMLScriptElement.supports_static", "HTMLScriptElement.supports()")}} یک سازوکار یکپارچه برای بررسی اینکه آیا مرورگر از انواع خاصی از اسکریپت‌ها پشتیبانی می‌کند فراهم می‌کند.

مثال زیر نحوهٔ بررسی پشتیبانی از ماژول‌ها را نشان می‌دهد و از وجود ویژگی `noModule` به عنوان راه‌حل جایگزین استفاده می‌کند.

```js
function checkModuleSupport() {
  if ("supports" in HTMLScriptElement) {
    return HTMLScriptElement.supports("module");
  }
  return "noModule" in document.createElement("script");
}
```

فرض بر این است که اسکریپت‌های کلاسیک در همهٔ مرورگرها پشتیبانی می‌شوند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- المان HTML {{HTMLElement("script")}}
- المان HTML {{HTMLElement("noscript")}}
- {{domxref("document.currentScript")}}
- [Web Workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers) (قطعه‌کدهای مشابه اسکریپت‌ها اما اجراشده در [زمینهٔ سراسری دیگری](/en-US/docs/Web/API/DedicatedWorkerGlobalScope))