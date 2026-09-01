---
title: "Fullscreen API"
slug: Web/API/Fullscreen_API
page-type: web-api-overview
browser-compat:
  - api.Document.fullscreenElement
  - api.Document.fullscreenEnabled
  - api.Document.exitFullscreen
  - api.Element.requestFullscreen
---

{{DefaultAPISidebar("Fullscreen API")}}

**Fullscreen API** روشهایی را ارائه میکند تا بتوان یک {{DOMxRef("Element")}} خاص (و زیرمجموعههای آن) را در حالت تمامصفحه (fullscreen) نمایش داد و پس از اتمام کار، از حالت تمامصفحه خارج شد. این امکان، ارائهی محتوای موردنظر—مانند یک بازی آنلاین—را با استفاده از کل صفحهی کاربر ممکن میسازد و تمام عناصر واسط کاربری مرورگر و سایر برنامهها را تا زمانی که حالت تمامصفحه خاموش نشده است، از صفحه حذف میکند.

برای جزئیات نحوهی استفاده از این API، مقالهی [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide) را ببینید.

## رابطها (Interfaces)

_Fullscreen API هیچ رابط اختصاصی خود را ندارد. در عوض، چند رابط دیگر را برای افزودن روشها، ویژگیها و مدیریتکنندههای رویداد لازم برای ارائهی قابلیت تمامصفحه، توسعه میدهد. این موارد در بخشهای زیر فهرست شدهاند._

## روشهای نمونه (Instance methods)

Fullscreen API روشهایی را به رابطهای {{DOMxRef("Document")}} و {{DOMxRef("Element")}} اضافه میکند تا امکان خاموش و روشن کردن حالت تمامصفحه فراهم شود.

### روشهای نمونه در رابط Document

- {{DOMxRef("Document.exitFullscreen()")}}
  - : درخواست میدهد که {{Glossary("user agent")}} از حالت تمامصفحه به حالت پنجره بازگردد. یک {{jsxref("Promise")}} برمیگرداند که پس از خاموش شدن کامل حالت تمامصفحه، حل میشود.

### روشهای نمونه در رابط Element

- {{DOMxRef("Element.requestFullscreen()")}}
  - : از عامل کاربر میخواهد که عنصر مشخصشده (و به تبع آن، زیرمجموعههای آن) را در حالت تمامصفحه قرار دهد و تمام عناصر UI مرورگر و همچنین همهی برنامههای دیگر را از صفحه حذف کند. یک {{jsxref("Promise")}} برمیگرداند که پس از فعال شدن حالت تمامصفحه، حل میشود.

## ویژگیهای نمونه (Instance properties)

- {{DOMxRef("Document.fullscreenElement")}} / {{DOMxRef("ShadowRoot.fullscreenElement")}}
  - : ویژگی `fullscreenElement` به شما میگوید که کدام {{DOMxRef("Element")}} در حال حاضر در حالت تمامصفحه در DOM (یا shadow DOM) نمایش داده میشود. اگر این مقدار `null` باشد، سند (یا shadow DOM) در حالت تمامصفحه نیست.
- {{DOMxRef("Document.fullscreenEnabled")}}
  - : ویژگی `fullscreenEnabled` به شما میگوید که آیا امکان فعال کردن حالت تمامصفحه وجود دارد یا خیر. اگر حالت تمامصفحه به هر دلیلی در دسترس نباشد (مانند مجاز نبودن ویژگی `"fullscreen"` یا پشتیبانی نشدن حالت تمامصفحه)، این مقدار `false` است.

### ویژگیهای منسوخ

- {{DOMxRef("Document.fullscreen")}} {{Deprecated_Inline}}
  - : یک مقدار بولی که اگر سند دارای عنصری باشد که در حال حاضر در حالت تمامصفحه نمایش داده میشود، `true` است؛ در غیر این صورت، `false` برمیگرداند.

  > [!NOTE]
  > به جای آن از ویژگی {{DOMxRef("Document.fullscreenElement", "fullscreenElement")}} در {{DOMxRef("Document")}} یا {{DOMxRef("ShadowRoot")}} استفاده کنید؛ اگر `null` نباشد، یک {{DOMxRef("Element")}} است که در حال حاضر در حالت تمامصفحه نمایش داده میشود.

## رویدادها (Events)

- {{domxref("Element/fullscreenchange_event", "fullscreenchange")}}
  - : به یک {{DOMxRef("Element")}} هنگام ورود یا خروج از حالت تمامصفحه ارسال میشود.
- {{domxref("Element/fullscreenerror_event", "fullscreenerror")}}
  - : اگر هنگام تلاش برای تغییر حالت یک `Element` به تمامصفحه یا خروج از آن خطایی رخ دهد، به آن ارسال میشود.

## کنترل دسترسی

دسترسی به حالت تمامصفحه را میتوان با استفاده از [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) کنترل کرد. ویژگی حالت تمامصفحه با رشتهی `"fullscreen"` شناسایی میشود و مقدار پیشفرض مجاز (allowlist) آن `"self"` است. این بدان معناست که حالت تمامصفحه در زمینههای سند سطح بالا و همچنین در زمینههای مرور تودرتو (nested browsing contexts) که از همان مبدأ سند بالایی بارگذاری شدهاند، مجاز است.

## نکات استفاده

کاربران میتوانند با فشردن کلید <kbd>ESC</kbd> (یا <kbd>F11</kbd>) از حالت تمامصفحه خارج شوند، بدون اینکه منتظر خروج برنامهریزیشدهی سایت یا برنامه باشند. مطمئن شوید که در جای مناسب از رابط کاربری خود، عناصر مناسبی قرار دادهاید که به کاربر اطلاع میدهد این گزینه در دسترس اوست.

> [!NOTE]
> پیمایش به صفحهی دیگر، تغییر تب، یا جابهجایی به برنامهی دیگر با استفاده از هر سوئیچکنندهی برنامه (یا <kbd>Alt</kbd>-<kbd>Tab</kbd>) نیز به ترک حالت تمامصفحه منجر میشود.

## مثالها

### استفادهی ساده از تمامصفحه

در این مثال، یک ویدیو در یک صفحهی وب نمایش داده میشود. فشردن کلید <kbd>Enter</kbd> به کاربر امکان میدهد بین نمایش پنجرهای و تمامصفحهی ویدیو جابهجا شود.

[مشاهدهی مثال زنده](https://mdn.github.io/dom-examples/fullscreen-api/index.html)

#### گوش دادن به کلید Enter

هنگام بارگذاری صفحه، این کد اجرا میشود تا یک شنوندهی رویداد برای نظارت بر کلید <kbd>Enter</kbd> تنظیم کند.

```js
const video = document.getElementById("video");

// با فشردن Enter، متد toggleFullScreen فراخوانی میشود
document.addEventListener("keydown", (e) => {
  if (e.key === "Enter") {
    toggleFullScreen(video);
  }
});
```

#### تغییر وضعیت تمامصفحه

این کد توسط مدیریتکنندهی رویداد بالا، زمانی که کاربر کلید <kbd>Enter</kbd> را فشار میدهد، فراخوانی میشود.

```js
function toggleFullScreen(video) {
  if (!document.fullscreenElement) {
    // اگر سند در حالت تمامصفحه نیست
    // ویدیو را تمامصفحه کن
    video.requestFullscreen();
  } else {
    // در غیر این صورت، از حالت تمامصفحه خارج شو
    document.exitFullscreen?.();
  }
}
```

این کار با بررسی مقدار ویژگی `fullscreenElement` در {{DOMxRef("Document", "document")}} شروع میشود. اگر مقدار `null` باشد، سند در حالت پنجره است، بنابراین باید به حالت تمامصفحه سوئیچ کنیم؛ در غیر این صورت، عنصر جاری در حالت تمامصفحه همان عنصر است. سوئیچ به حالت تمامصفحه با فراخوانی {{DOMxRef("Element.requestFullscreen()")}} روی عنصر {{HTMLElement("video")}} انجام میشود.

اگر حالت تمامصفحه از قبل فعال است (`fullscreenElement` برابر `null` نیست)، {{DOMxRef("Document.exitFullscreen", "exitFullscreen()")}} را روی `document` فراخوانی میکنیم تا حالت تمامصفحه خاموش شود.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMxRef("Element.requestFullscreen()")}}
- {{DOMxRef("Document.exitFullscreen()")}}
- {{DOMxRef("Document.fullscreen")}}
- {{DOMxRef("Document.fullscreenElement")}}
- {{CSSxRef(":fullscreen")}}, {{CSSxRef("::backdrop")}}
- [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen)