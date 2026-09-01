---
title: "Document"
---

---
title: Document
slug: Web/API/Document
page-type: web-api-interface
browser-compat: api.Document
---

{{APIRef("DOM")}}

رابطهٔ **`Document`** هر صفحهٔ وب بارگذاری‌شده در مرورگر را نمایش می‌دهد و به عنوان نقطهٔ ورود به محتوای صفحهٔ وب عمل می‌کند که همان [درخت DOM](/en-US/docs/Web/API/Document_Object_Model#what_is_a_dom_tree) است.

درخت DOM شامل عناصری مانند {{HTMLElement("body")}} و {{HTMLElement("table")}} و [بسیاری عناصر دیگر](/en-US/docs/Web/HTML/Reference/Elements) است. این رابط قابلیت‌هایی را به‌صورت سراسری در اختیار سند قرار می‌دهد؛ مانند نحوهٔ به‌دست‌آوردن آدرس صفحه و ایجاد عناصر جدید در سند.

{{InheritanceDiagram}}

رابطهٔ `Document` ویژگی‌ها و روش‌های مشترک را برای هر نوع سندی توصیف می‌کند. بسته به نوع سند (مثلاً [HTML](/en-US/docs/Web/HTML)، [XML](/en-US/docs/Web/XML)، SVG و ...)، یک API گسترده‌تر در دسترس است: اسناد HTML که با نوع محتوای `"text/html"` ارائه می‌شوند، همچنین رابط {{DOMxRef("HTMLDocument")}} را پیاده‌سازی می‌کنند، در حالی که اسناد XML و SVG رابط {{DOMxRef("XMLDocument")}} را پیاده‌سازی می‌کنند.

## سازنده

- {{DOMxRef("Document.Document", "Document()")}}
  - : یک شیء `Document` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین از رابط‌های {{DOMxRef("Node")}} و {{DOMxRef("EventTarget")}} ارث‌بری می‌کند._

- {{DOMxRef("Document.activeElement")}} {{ReadOnlyInline}}
  - : {{DOMxRef('Element')}} ای را برمی‌گرداند که در حال حاضر فوکوس دارد.
- {{DOMxRef("Document.activeViewTransition")}} {{ReadOnlyInline}}
  - : یک نمونه {{DOMxRef('ViewTransition')}} را برمی‌گرداند که نمایانگر [گذر نما](/en-US/docs/Web/API/View_Transition_API) در حال حاضر فعال در سند است، یا اگر هیچ گذر نمای فعالی وجود نداشته باشد، `null` برمی‌گرداند.
- {{DOMxRef("Document.adoptedStyleSheets")}}
  - : یک آرایه از شیوه‌نامه‌های ساخته‌شده (constructed stylesheets) را برای استفاده در سند اضافه می‌کند. این شیوه‌نامه‌ها می‌توانند با زیردرخت‌های shadow DOM همین سند نیز به اشتراک گذاشته شوند.
- {{DOMxRef("Document.body")}}
  - : گرهٔ {{HTMLElement("body")}} یا {{htmlelement("frameset")}} سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.characterSet")}} {{ReadOnlyInline}}
  - : مجموعه‌کاراکتر مورد استفادهٔ سند را برمی‌گرداند.
- {{domxref("Document.childElementCount")}} {{ReadOnlyInline}}
  - : تعداد عناصر فرزند سند فعلی را برمی‌گرداند.
- {{domxref("Document.children")}} {{ReadOnlyInline}}
  - : عناصر فرزند سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.compatMode")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که سند در حالت _quirks_ (سازگاری) یا _strict_ (سخت‌گیرانه) رندر می‌شود.
- {{DOMxRef("Document.contentType")}} {{ReadOnlyInline}}
  - : نوع محتوا (Content-Type) را از هدر MIME سند فعلی برمی‌گرداند.
- {{DOMxRef("Document.currentScript")}} {{ReadOnlyInline}}
  - : عنصر {{HTMLElement("script")}}ای را برمی‌گرداند که اسکریپت آن در حال حاضر در حال پردازش است و [یک ماژول جاوااسکریپت نیست](https://github.com/whatwg/html/issues/997).
- {{DOMxRef("Document.customElementRegistry")}} {{ReadOnlyInline}}
  - : شیء {{domxref("CustomElementRegistry")}} مرتبط با این سند را برمی‌گرداند، یا اگر تنظیم نشده باشد `null` برمی‌گرداند.
- {{DOMxRef("Document.doctype")}} {{ReadOnlyInline}}
  - : تعریف نوع سند (DTD) سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.documentElement")}} {{ReadOnlyInline}}
  - : {{DOMxRef("Element")}}ای را برمی‌گرداند که فرزند مستقیم سند است. برای اسناد HTML، این معمولاً شیء {{DOMxRef("HTMLHtmlElement")}} است که عنصر {{HTMLElement("html")}} سند را نمایش می‌دهد.
- {{DOMxRef("Document.documentURI")}} {{ReadOnlyInline}}
  - : مکان سند را به صورت رشته برمی‌گرداند.
- {{DOMxRef("Document.embeds")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} از عناصر جاسازی‌شدهٔ {{HTMLElement('embed')}} در سند را برمی‌گرداند.
- {{DOMxRef("Document.featurePolicy")}} {{Experimental_Inline}} {{ReadOnlyInline}} {{non-standard_inline}}
  - : رابط {{DOMxRef("FeaturePolicy")}} را با سیاست‌های ویژگی اعمال‌شده بر سند برمی‌گرداند.
- {{domxref("Document.firstElementChild")}} {{ReadOnlyInline}}
  - : اولین عنصر فرزند سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.fonts")}}
  - : رابط {{DOMxRef("FontFaceSet")}} سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.forms")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} از عناصر {{HTMLElement("form")}} در سند را برمی‌گرداند.
- {{DOMxRef("Document.fragmentDirective")}} {{ReadOnlyInline}}
  - : {{domxref("FragmentDirective")}} سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.fullscreenElement")}} {{ReadOnlyInline}}
  - : عنصری که در حال حاضر در حالت تمام‌صفحه برای این سند قرار دارد.
- {{DOMxRef("Document.head")}} {{ReadOnlyInline}}
  - : عنصر {{HTMLElement("head")}} سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.hidden")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد صفحه پنهان در نظر گرفته می‌شود یا نه.
- {{DOMxRef("Document.images")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} از تصاویر موجود در سند را برمی‌گرداند.
- {{DOMxRef("Document.implementation")}} {{ReadOnlyInline}}
  - : پیاده‌سازی DOM مرتبط با سند فعلی را برمی‌گرداند.
- {{domxref("Document.lastElementChild")}} {{ReadOnlyInline}}
  - : آخرین عنصر فرزند سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.links")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} از پیوندهای موجود در سند را برمی‌گرداند.
- {{DOMxRef("Document.pictureInPictureElement")}} {{ReadOnlyInline}}
  - : {{DOMxRef('Element')}}ای را که در حال حاضر در حالت تصویر-در-تصویر (picture-in-picture) در این سند نمایش داده می‌شود، برمی‌گرداند.
- {{DOMxRef("Document.pictureInPictureEnabled")}} {{ReadOnlyInline}}
  - : اگر ویژگی تصویر-در-تصویر فعال باشد، `true` برمی‌گرداند.
- {{DOMxRef("Document.plugins")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} از افزونه‌های موجود را برمی‌گرداند.
- {{DOMxRef("Document.pointerLockElement")}} {{ReadOnlyInline}}
  - : عنصری را که به عنوان هدف رویدادهای ماوس در حالی که اشاره‌گر قفل شده است تنظیم شده، برمی‌گرداند. اگر قفل در انتظار باشد، اشاره‌گر قفل نباشد، یا هدف در سند دیگری باشد، `null` برمی‌گرداند.
- {{DOMxRef("Document.prerendering")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا سند در حال حاضر در فرآیند پیش‌رندر (prerendering) است، به گونه‌ای که از طریق [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) آغاز شده است.
- {{DOMxRef("Document.scripts")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} از عناصر {{HTMLElement("script")}} در سند را برمی‌گرداند.
- {{DOMxRef("Document.scrollingElement")}} {{ReadOnlyInline}}
  - : ارجاعی به {{DOMxRef("Element")}}ای که سند را اسکرول می‌کند برمی‌گرداند.
- {{DOMxRef("Document.styleSheets")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef('StyleSheetList')}} از اشیاء {{DOMxRef('CSSStyleSheet')}} برای شیوه‌نامه‌هایی که به‌صریح به سند پیوند داده شده‌اند یا در آن جاسازی شده‌اند، برمی‌گرداند.
- {{DOMxRef("Document.timeline")}} {{ReadOnlyInline}}
  - : خط زمانی را به عنوان یک نمونهٔ ویژه از {{domxref("DocumentTimeline")}} برمی‌گرداند که به‌طور خودکار هنگام بارگذاری صفحه ایجاد می‌شود.
- {{DOMxRef("Document.visibilityState")}} {{ReadOnlyInline}}
  - : یک `string` برمی‌گرداند که وضعیت دید سند را نشان می‌دهد. مقادیر احتمالی: `visible`، `hidden` و `unloaded` هستند.

### افزونه‌های مربوط به HTMLDocument

_رابط `Document` برای اسناد HTML از رابط {{DOMxRef("HTMLDocument")}} ارث‌بری می‌کند یا برای چنین اسنادی گسترش می‌یابد._

- {{DOMxRef("Document.cookie")}}
  - : فهرستی از کوکی‌های آن سند را که با سمی‌کالن جدا شده‌اند برمی‌گرداند یا یک کوکی واحد تنظیم می‌کند.
- {{DOMxRef("Document.defaultView")}} {{ReadOnlyInline}}
  - : ارجاعی به شیء پنجره (window) برمی‌گرداند.
- {{DOMxRef("Document.designMode")}}
  - : قابلیت ویرایش کل سند را می‌خواند/تنظیم می‌کند.
- {{DOMxRef("Document.dir")}}
  - : جهت (rtl/ltr) سند را می‌خواند/تنظیم می‌کند.
- {{DOMxRef("Document.fullscreenEnabled")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا حالت تمام‌صفحه در دسترس است یا نه.
- {{DOMxRef("Document.lastModified")}} {{ReadOnlyInline}}
  - : تاریخی را که سند آخرین بار تغییر کرده است برمی‌گرداند.
- {{DOMxRef("Document.location")}} {{ReadOnlyInline}}
  - : URI سند فعلی را برمی‌گرداند.
- {{DOMxRef("Document.readyState")}} {{ReadOnlyInline}}
  - : وضعیت بارگذاری سند را برمی‌گرداند.
- {{DOMxRef("Document.referrer")}} {{ReadOnlyInline}}
  - : URI صفحه‌ای که به این صفحه پیوند داده است را برمی‌گرداند.
- {{DOMxRef("Document.title")}}
  - : عنوان سند فعلی را تنظیم یا برمی‌گرداند.
- {{DOMxRef("Document.URL")}} {{ReadOnlyInline}}
  - : مکان سند را به صورت رشته برمی‌گرداند.
- ویژگی‌های نام‌دار (Named properties)
  - : برخی عناصر در سند نیز به عنوان ویژگی در دسترس هستند:
    - برای هر عنصر {{HTMLElement("embed")}}، {{HTMLElement("form")}}، {{HTMLElement("iframe")}}، {{HTMLElement("img")}} و {{HTMLElement("object")}}، ویژگی `name` آن (اگر غیرخالی باشد) در دسترس قرار می‌گیرد. مثلاً اگر سند شامل `<form name="my_form">` باشد، آنگاه `document["my_form"]` (و معادل آن `document.my_form`) ارجاعی به آن عنصر برمی‌گرداند.
    - برای هر عنصر {{HTMLElement("object")}}، ویژگی `id` آن (اگر غیرخالی باشد) در دسترس قرار می‌گیرد.
    - برای هر عنصر {{HTMLElement("img")}} با `name` غیرخالی، ویژگی `id` آن (اگر غیرخالی باشد) در دسترس قرار می‌گیرد.

    اگر یک ویژگی با یک عنصر واحد مطابقت داشته باشد، همان عنصر مستقیماً بازگردانده می‌شود. اگر آن عنصر واحد یک iframe باشد، به جای آن {{domxref("HTMLIFrameElement/contentWindow", "contentWindow")}} آن بازگردانده می‌شود. اگر ویژگی با چند عنصر مطابقت داشته باشد، یک {{domxref("HTMLCollection")}} شامل همهٔ آن‌ها بازگردانده می‌شود.

### ویژگی‌های منسوخ‌شده

- {{DOMxRef("Document.alinkColor")}} {{Deprecated_Inline}}
  - : رنگ پیوندهای فعال در بدنهٔ سند را برمی‌گرداند یا تنظیم می‌کند.
- {{DOMxRef("Document.all")}} {{Deprecated_Inline}}
  - : دسترسی به همهٔ عناصر سند را فراهم می‌کند — یک {{DOMxRef('HTMLAllCollection')}} برمی‌گرداند که ریشه در گره سند دارد. این یک ویژگی قدیمی و غیراستاندارد است و نباید استفاده شود.
- {{DOMxRef("Document.anchors")}} {{Deprecated_Inline}} {{ReadOnlyInline}}
  - : فهرستی از همهٔ لنگرها (anchors) در سند را برمی‌گرداند.
- {{DOMxRef("Document.applets")}} {{Deprecated_Inline}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLCollection")}} خالی برمی‌گرداند. ویژگی قدیمی‌ای که قبلاً فهرست اپلت‌های درون سند را برمی‌گرداند.
- {{DOMxRef("Document.bgColor")}} {{Deprecated_Inline}}
  - : رنگ پس‌زمینهٔ سند فعلی را می‌خواند/تنظیم می‌کند.
- {{DOMxRef("Document.characterSet","Document.charset")}} {{Deprecated_Inline}} {{ReadOnlyInline}}
  - : نام مستعار {{DOMxRef("Document.characterSet")}}. به جای آن از این ویژگی استفاده کنید.
- {{DOMxRef("Document.domain")}} {{Deprecated_Inline}}
  - : دامنهٔ سند فعلی را می‌خواند/تنظیم می‌کند.
- {{DOMxRef("Document.fgColor")}} {{Deprecated_Inline}}
  - : رنگ پیش‌زمینه یا رنگ متن سند فعلی را می‌خواند/تنظیم می‌کند.
- {{DOMxRef("Document.fullscreen")}} {{Deprecated_Inline}}
  - : وقتی سند در [حالت تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API) است، `true` برمی‌گرداند.
- {{DOMxRef("Document.characterSet", "Document.inputEncoding")}} {{Deprecated_Inline}} {{ReadOnlyInline}}
  - : نام مستعار {{DOMxRef("Document.characterSet")}}. به جای آن از این ویژگی استفاده کنید.
- {{DOMxRef("Document.lastStyleSheetSet")}} {{Deprecated_Inline}} {{ReadOnlyInline}} {{Non-standard_Inline}}
  - : نام مجموعه‌شیوه‌نامه‌ای را که آخرین بار فعال شده است برمی‌گرداند. تا زمانی که مجموعه‌شیوه‌نامه با تنظیم مقدار {{DOMxRef("Document.selectedStyleSheetSet","selectedStyleSheetSet")}} تغییر نکند، مقدار `null` دارد.
- {{DOMxRef("Document.linkColor")}} {{Deprecated_Inline}}
  - : رنگ پیوندها در سند را می‌خواند/تنظیم می‌کند.
- {{