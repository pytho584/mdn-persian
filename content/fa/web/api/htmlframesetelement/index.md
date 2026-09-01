---
title: HTMLFrameSetElement
slug: Web/API/HTMLFrameSetElement
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.HTMLFrameSetElement
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

رابطهٔ **`HTMLFrameSetElement`** ویژگی‌های خاصی را (فراتر از ویژگی‌های رابط معمولی {{domxref("HTMLElement")}} که از آن ارث می‌برد) برای دستکاری عناصر {{HTMLElement("frameset")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLFrameSetElement.cols")}} {{deprecated_inline}}
  - : رشته‌ای به صورت فهرستی جدا شده با کاما که عرض هر ستون را در یک frameset مشخص می‌کند.
- {{domxref("HTMLFrameSetElement.rows")}} {{deprecated_inline}}
  - : رشته‌ای به صورت فهرستی جدا شده با کاما که ارتفاع هر ستون را در یک frameset مشخص می‌کند.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مدیریت‌کننده‌های رویداد

رویدادهای {{domxref("HTMLElement")}} به ارث می‌رسند.

ویژگی‌های مدیریت‌کننده رویداد `onXYZ` زیر از {{domxref("Window")}} نیز به عنوان نام‌های مستعار در دسترس هستند که هدف آن‌ها شیء `window` است. با این حال، توصیه می‌شود به جای `HTMLFrameSetElement` مستقیماً به شیء `window` گوش دهید.

> [!NOTE]
> استفاده از `addEventListener()` روی `HTMLFrameSetElement` برای مدیریت‌کننده‌های رویداد `onXYZ` فهرست‌شده در زیر کار نخواهد کرد. به جای آن، به رویدادها روی شیء {{domxref("window")}} گوش دهید.

- {{domxref("window.afterprint_event", "HTMLFrameSetElement.onafterprint")}}
  - : پس از شروع چاپ سند مرتبط یا بسته شدن پیش‌نمایش چاپ، فعال می‌شود.
- {{domxref("window.beforeprint_event", "HTMLFrameSetElement.onbeforeprint")}}
  - : هنگامی که سند مرتبط در آستانه چاپ یا پیش‌نمایش برای چاپ است، فعال می‌شود.
- {{domxref("window.beforeunload_event", "HTMLFrameSetElement.onbeforeunload")}}
  - : هنگامی که پنجره، سند و منابع آن در آستانه تخلیه (unload) هستند، فعال می‌شود.
- {{domxref("window.gamepadconnected_event", "HTMLFrameSetElement.ongamepadconnected")}}
  - : هنگامی که مرورگر تشخیص می‌دهد یک گیم‌پد متصل شده یا اولین بار که یک دکمه/محور از گیم‌پد استفاده می‌شود، فعال می‌شود.
- {{domxref("window.gamepaddisconnected_event", "HTMLFrameSetElement.ongamepaddisconnected")}}
  - : هنگامی که مرورگر تشخیص می‌دهد یک گیم‌پد قطع شده است، فعال می‌شود.
- {{domxref("window.hashchange_event", "HTMLFrameSetElement.onhashchange")}}
  - : هنگامی که شناسه تکه‌ای (fragment identifier) URL تغییر می‌کند (بخشی از URL که با نماد `#` شروع شده و پس از آن می‌آید)، فعال می‌شود.
- {{domxref("window.languagechange_event", "HTMLFrameSetElement.onlanguagechange")}}
  - : هنگامی که زبان ترجیحی کاربر تغییر می‌کند، فعال می‌شود.
- {{domxref("window.message_event", "HTMLFrameSetElement.onmessage")}}
  - : هنگامی که پنجره پیامی دریافت می‌کند، برای مثال از فراخوانی [`Window.postMessage()`](/en-US/docs/Web/API/Window/postMessage) از یک بافت مرور دیگر، فعال می‌شود.
- {{domxref("window.messageerror_event", "HTMLFrameSetElement.onmessageerror")}}
  - : هنگامی که پنجره پیامی دریافت می‌کند که نمی‌توان آن را از حالت سریالی (deserialize) خارج کرد، فعال می‌شود.
- {{domxref("window.offline_event", "HTMLFrameSetElement.onoffline")}}
  - : هنگامی که مرورگر دسترسی خود به شبکه را از دست می‌دهد و مقدار {{domxref("Navigator.onLine")}} به `false` تغییر می‌کند، فعال می‌شود.
- {{domxref("window.online_event", "HTMLFrameSetElement.ononline")}}
  - : هنگامی که مرورگر به شبکه دسترسی پیدا می‌کند و مقدار {{domxref("Navigator.onLine")}} به `true` تغییر می‌کند، فعال می‌شود.
- {{domxref("window.pagehide_event", "HTMLFrameSetElement.onpagehide")}}
  - : هنگامی که مرورگر صفحه فعلی را در فرآیند نمایش صفحه‌ای دیگر از تاریخچه جلسه پنهان می‌کند، فعال می‌شود.
- {{domxref("window.pageshow_event", "HTMLFrameSetElement.onpageshow")}}
  - : هنگامی که مرورگر سند پنجره را به دلیل ناوبری نمایش می‌دهد، فعال می‌شود.
- {{domxref("window.popstate_event", "HTMLFrameSetElement.onpopstate")}}
  - : هنگامی که ورودی تاریخچه فعال در حالی که کاربر در تاریخچه جلسه حرکت می‌کند تغییر می‌کند، فعال می‌شود.
- {{domxref("window.rejectionhandled_event", "HTMLFrameSetElement.onrejectionhandled")}}
  - : هر زمان که یک {{jsxref("Promise")}} جاوااسکریپت رد شود و این رد شدن مدیریت شده باشد، فعال می‌شود.
- {{domxref("window.storage_event", "HTMLFrameSetElement.onstorage")}}
  - : هنگامی که یک ناحیه ذخیره‌سازی (`localStorage`) در بافت سند دیگری تغییر کند، فعال می‌شود.
- {{domxref("window.unhandledrejection_event", "HTMLFrameSetElement.onunhandledrejection")}}
  - : هر زمان که یک {{jsxref("Promise")}} رد شود اما این رد شدن مدیریت نشده باشد، فعال می‌شود.
- {{domxref("window.unload_event", "HTMLFrameSetElement.onunload")}}
  - : هنگامی که سند در حال تخلیه (unload) است، فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("frameset")}}
- معادل این عنصر خارج از فریم‌ها: `HTMLFrameSetElement`.