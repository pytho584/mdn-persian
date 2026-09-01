---
title: HTMLBodyElement
slug: Web/API/HTMLBodyElement
page-type: web-api-interface
browser-compat: api.HTMLBodyElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLBodyElement`** ویژگی‌های خاصی (فراتر از آنچه از رابط معمولی {{ domxref("HTMLElement") }} به ارث برده است) را برای دستکاری عناصر {{HtmlElement("body")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLBodyElement.aLink")}} {{deprecated_inline}}
  - : یک رشته که رنگ پیوند‌های فعال را نشان می‌دهد.
- {{domxref("HTMLBodyElement.background")}} {{deprecated_inline}}
  - : یک رشته که توضیح مکان منبع تصویر پس‌زمینه را نشان می‌دهد. توجه داشته باشید که این یک URI نیست، اگرچه برخی از نسخه‌های قدیمی برخی مرورگرها آن را به عنوان URI انتظار دارند.
- {{domxref("HTMLBodyElement.bgColor")}} {{deprecated_inline}}
  - : یک رشته که رنگ پس‌زمینه سند را نشان می‌دهد.
- {{domxref("HTMLBodyElement.link")}} {{deprecated_inline}}
  - : یک رشته که رنگ پیوند‌های بازدید نشده را نشان می‌دهد.
- {{domxref("HTMLBodyElement.text")}} {{deprecated_inline}}
  - : یک رشته که رنگ پیش‌زمینه متن را نشان می‌دهد.
- {{domxref("HTMLBodyElement.vLink")}} {{deprecated_inline}}
  - : یک رشته که رنگ پیوند‌های بازدید شده را نشان می‌دهد.

## روش‌های نمونه

_بدون روش خاص؛ روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مدیریت‌کننده‌های رویداد

رویدادهای {{domxref("HTMLElement")}} به ارث می‌رسند.

ویژگی‌های مدیریت‌کننده رویداد `onXYZ` زیر از {{domxref("Window")}} نیز به عنوان نام‌های مستعار در دسترس هستند که به شیء `window` اشاره می‌کنند. با این حال، توصیه می‌شود که مستقیماً به رویدادهای روی شیء `window` گوش دهید، نه روی `HTMLBodyElement`.

> [!NOTE]
> استفاده از `addEventListener()` روی `HTMLBodyElement` برای مدیریت‌کننده‌های رویداد `onXYZ` فهرست شده در زیر کار نخواهد کرد. در عوض، به رویدادهای روی شیء {{domxref("window")}} گوش دهید.

- {{domxref("window.afterprint_event", "HTMLBodyElement.onafterprint")}}
  - : زمانی که چاپ سند مرتبط شروع شده یا پیش‌نمایش چاپ بسته شده است، فعال می‌شود.
- {{domxref("window.beforeprint_event", "HTMLBodyElement.onbeforeprint")}}
  - : زمانی که سند مرتبط در شرف چاپ یا پیش‌نمایش برای چاپ است، فعال می‌شود.
- {{domxref("window.beforeunload_event", "HTMLBodyElement.onbeforeunload")}}
  - : زمانی که پنجره، سند و منابع آن در شرف تخلیه هستند، فعال می‌شود.
- {{domxref("window.blur_event", "HTMLBodyElement.onblur")}}
  - : زمانی که پنجره فوکوس خود را از دست می‌دهد، فعال می‌شود.
- {{domxref("window.error_event", "HTMLBodyElement.onerror")}}
  - : زمانی که خطایی رخ می‌دهد و به سمت پنجره بالا می‌آید، فعال می‌شود.
- {{domxref("window.focus_event", "HTMLBodyElement.onfocus")}}
  - : زمانی که پنجره فوکوس می‌گیرد، فعال می‌شود.
- {{domxref("window.gamepadconnected_event", "HTMLBodyElement.ongamepadconnected")}}
  - : زمانی که مرورگر تشخیص می‌دهد یک گیم‌پد متصل شده است یا اولین بار که یک دکمه/محور از گیم‌پد استفاده می‌شود، فعال می‌شود.
- {{domxref("window.gamepaddisconnected_event", "HTMLBodyElement.ongamepaddisconnected")}}
  - : زمانی که مرورگر تشخیص می‌دهد یک گیم‌پد قطع شده است، فعال می‌شود.
- {{domxref("window.hashchange_event", "HTMLBodyElement.onhashchange")}}
  - : زمانی که شناسه قطعه URL تغییر می‌کند (بخشی از URL که با نماد `#` شروع می‌شود و پس از آن می‌آید)، فعال می‌شود.
- {{domxref("window.languagechange_event", "HTMLBodyElement.onlanguagechange")}}
  - : زمانی که زبان ترجیحی کاربر تغییر می‌کند، فعال می‌شود.
- {{domxref("window.load_event", "HTMLBodyElement.onload")}}
  - : زمانی که بارگذاری سند به پایان رسیده است، فعال می‌شود.
- {{domxref("window.message_event", "HTMLBodyElement.onmessage")}}
  - : زمانی که پنجره یک پیام دریافت می‌کند، مثلاً از یک فراخوانی [`Window.postMessage()`](/en-US/docs/Web/API/Window/postMessage) از یک زمینه مرور دیگر، فعال می‌شود.
- {{domxref("window.messageerror_event", "HTMLBodyElement.onmessageerror")}}
  - : زمانی که پنجره پیامی دریافت می‌کند که قابل deserialize نیست، فعال می‌شود.
- {{domxref("window.offline_event", "HTMLBodyElement.onoffline")}}
  - : زمانی که مرورگر دسترسی به شبکه را از دست داده است و مقدار {{domxref("Navigator.onLine")}} به `false` تغییر می‌کند، فعال می‌شود.
- {{domxref("window.online_event", "HTMLBodyElement.ononline")}}
  - : زمانی که مرورگر دسترسی به شبکه پیدا کرده است و مقدار {{domxref("Navigator.onLine")}} به `true` تغییر می‌کند، فعال می‌شود.
- {{domxref("window.pagehide_event", "HTMLBodyElement.onpagehide")}}
  - : زمانی که مرورگر صفحه فعلی را در فرآیند نمایش یک صفحه متفاوت از تاریخچه جلسه پنهان می‌کند، فعال می‌شود.
- {{domxref("window.pageshow_event", "HTMLBodyElement.onpageshow")}}
  - : زمانی که مرورگر سند پنجره را به دلیل ناوبری نمایش می‌دهد، فعال می‌شود.
- {{domxref("window.popstate_event", "HTMLBodyElement.onpopstate")}}
  - : زمانی که ورودی تاریخچه فعال در حین ناوبری کاربر در تاریخچه جلسه تغییر می‌کند، فعال می‌شود.
- {{domxref("window.rejectionhandled_event", "HTMLBodyElement.onrejectionhandled")}}
  - : هر زمان که یک {{jsxref("Promise")}} جاوااسکریپت رد شود و رد شدن مدیریت شده باشد، فعال می‌شود.
- {{domxref("window.resize_event", "HTMLBodyElement.onresize")}}
  - : زمانی که نمای سند تغییر اندازه داده شده است، فعال می‌شود.
- {{domxref("window.scroll_event", "HTMLBodyElement.onscroll")}}
  - : زمانی که نمای سند یا یک عنصر اسکرول شده است، فعال می‌شود.
- {{domxref("window.storage_event", "HTMLBodyElement.onstorage")}}
  - : زمانی که یک ناحیه ذخیره‌سازی (`localStorage`) در زمینه یک سند دیگر تغییر یافته است، فعال می‌شود.
- {{domxref("window.unhandledrejection_event", "HTMLBodyElement.onunhandledrejection")}}
  - : هر زمان که یک {{jsxref("Promise")}} رد شود اما رد شدن مدیریت نشده باشد، فعال می‌شود.
- {{domxref("window.unload_event", "HTMLBodyElement.onunload")}}
  - : زمانی که سند در حال تخلیه است، فعال می‌شود.

توجه داشته باشید که اگرچه `onblur`، `onerror`، `onfocus`، `onload`، `onresize` و `onscroll` روی هر عنصری در دسترس هستند، معانی آنها روی عنصر `<body>` با عناصر دیگر یکسان نیست. آنها به جای آن به رویدادهای روی شیء `window` گوش می‌دهند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("body") }}