---
title: "HTMLIFrameElement"
slug: Web/API/HTMLIFrameElement
page-type: web-api-interface
browser-compat: api.HTMLIFrameElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLIFrameElement`** ویژگی‌ها و روش‌های خاصی (فراتر از آنچه از رابط {{domxref("HTMLElement")}} به ارث برده است) برای دستکاری طرح و ارائه عناصر فریم درون‌خطی فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLIFrameElement.align")}} {{Deprecated_Inline}}
  - : رشته‌ای که تراز فریم را نسبت به زمینه اطراف مشخص می‌کند.
- {{domxref("HTMLIFrameElement.allow")}}
  - : رشته‌ای که [سیاست مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مشخص‌شده برای این `<iframe>` را نشان می‌دهد.
- {{domxref("HTMLIFrameElement.allowFullscreen")}}
  - : یک مقدار بولی که نشان می‌دهد آیا فریم درون‌خطی مایل به قرار گرفتن در حالت تمام‌صفحه است. برای جزئیات به [استفاده از حالت تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API) مراجعه کنید.
- {{domxref("HTMLIFrameElement.allowPaymentRequest")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا [API درخواست پرداخت](/en-US/docs/Web/API/Payment_Request_API) می‌تواند درون یک iframe با منشأ متفاوت فراخوانی شود.
- {{domxref("HTMLIFrameElement.browsingTopics")}} {{non-standard_inline}} {{deprecated_inline}}
  - : یک ویژگی بولی که مشخص می‌کند موضوعات انتخاب‌شده برای کاربر فعلی باید با درخواست منبع {{htmlelement("iframe")}} مرتبط ارسال شود. این مقدار ویژگی محتوای `browsingtopics` را منعکس می‌کند.
- {{domxref("HTMLIFrameElement.contentDocument")}} {{ReadOnlyInline}}
  - : یک {{domxref("Document")}}، یعنی سند فعال در زمینه مرور تودرتو فریم درون‌خطی را برمی‌گرداند.
- {{domxref("HTMLIFrameElement.contentWindow")}} {{ReadOnlyInline}}
  - : یک {{glossary("WindowProxy")}}، یعنی پروکسی پنجره برای زمینه مرور تودرتو را برمی‌گرداند.
- {{domxref("HTMLIFrameElement.credentialless")}} {{Experimental_Inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا `<iframe>` بدون اعتبار (credentialless) است، به این معنی که محتوای آن در یک زمینه جدید و موقت بارگذاری می‌شود. این زمینه به ذخیره‌سازی مشترک و اعتبارنامه‌های زمینه والد دسترسی ندارد. در عوض، قوانین جاسازی {{httpheader("Cross-Origin-Embedder-Policy")}} (COEP) می‌توانند لغو شوند، بنابراین اسنادی که COEP را تنظیم کرده‌اند می‌توانند اسناد شخص ثالثی را که این قوانین را ندارند جاسازی کنند. برای توضیح بیشتر [IFrame credentialless](/en-US/docs/Web/HTTP/Guides/IFrame_credentialless) را ببینید.
- {{domxref("HTMLIFrameElement.csp")}} {{Experimental_Inline}}
  - : سیاست امنیت محتوا (Content Security Policy) را مشخص می‌کند که یک سند جاسازی‌شده باید موافقت کند آن را بر خود اعمال کند.
- {{domxref("HTMLIFrameElement.featurePolicy")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{non-standard_inline}}
  - : رابط {{domxref("FeaturePolicy")}} را برمی‌گرداند که یک API ساده برای بازرسی [سیاست‌های مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) اعمال‌شده بر یک سند خاص فراهم می‌کند.
- {{domxref("HTMLIFrameElement.frameBorder")}} {{Deprecated_Inline}}
  - : رشته‌ای که نشان می‌دهد آیا بین فریم‌ها حاشیه ایجاد شود.
- {{domxref("HTMLIFrameElement.height")}}
  - : رشته‌ای که ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/iframe#height) را منعکس می‌کند و ارتفاع فریم را نشان می‌دهد.
- {{domxref("HTMLIFrameElement.loading")}}
  - : رشته‌ای که به مرورگر راهنمایی می‌کند iframe باید فوراً (`eager`) یا بر اساس نیاز (`lazy`) بارگذاری شود. این ویژگی مقدار [`loading`](/en-US/docs/Web/HTML/Reference/Elements/iframe#loading) HTML را منعکس می‌کند.
- {{domxref("HTMLIFrameElement.longDesc")}} {{Deprecated_Inline}}
  - : رشته‌ای که URI یک توضیح طولانی از فریم را شامل می‌شود.
- {{domxref("HTMLIFrameElement.marginHeight")}} {{Deprecated_Inline}}
  - : رشته‌ای که ارتفاع حاشیه فریم است.
- {{domxref("HTMLIFrameElement.marginWidth")}} {{Deprecated_Inline}}
  - : رشته‌ای که عرض حاشیه فریم است.
- {{domxref("HTMLIFrameElement.name")}}
  - : رشته‌ای که ویژگی HTML [`name`](/en-US/docs/Web/HTML/Reference/Elements/iframe#name) را منعکس می‌کند و شامل نامی است که با آن می‌توان به فریم ارجاع داد.
- {{domxref("HTMLIFrameElement.privateToken")}} {{experimental_inline}}
  - : یک نمایش رشته‌ای از یک شیء گزینه‌ها که یک عملیات [نشانه وضعیت خصوصی](/en-US/docs/Web/API/Private_State_Token_API/Using) را نشان می‌دهد؛ این شیء همان ساختار ویژگی [`privateToken`](/en-US/docs/Web/API/RequestInit#privatetoken) در فرهنگ لغت `RequestInit` را دارد. محتوای ویژگی [`privateToken`](/en-US/docs/Web/HTML/Reference/Elements/iframe#privatetoken) عنصر `<iframe>` مرتبط را منعکس می‌کند.
- {{domxref("HTMLIFrameElement.referrerPolicy")}}
  - : رشته‌ای که ویژگی HTML [`referrerPolicy`](/en-US/docs/Web/HTML/Reference/Elements/iframe#referrerpolicy) را منعکس می‌کند و نشان می‌دهد هنگام واکشی منبع پیوندداده‌شده از کدام ارجاع‌دهنده استفاده شود.
- {{domxref("HTMLIFrameElement.sandbox")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} برمی‌گرداند که ویژگی HTML [`sandbox`](/en-US/docs/Web/HTML/Reference/Elements/iframe#sandbox) را منعکس می‌کند و محدودیت‌های اضافی بر رفتار محتوای تودرتو نشان می‌دهد.
- {{domxref("HTMLIFrameElement.scrolling")}} {{Deprecated_Inline}}
  - : رشته‌ای که نشان می‌دهد آیا مرورگر باید برای فریم نوارهای پیمایش ارائه دهد.
- {{domxref("HTMLIFrameElement.src")}}
  - : رشته‌ای که ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/iframe#src) را منعکس می‌کند و شامل آدرس محتوایی است که باید جاسازی شود. توجه داشته باشید که حذف برنامه‌ریزی‌شده ویژگی src یک `<iframe>` (مثلاً از طریق {{domxref("Element.removeAttribute()")}}) باعث می‌شود `about:blank` در فریم در Firefox (از نسخه 65)، مرورگرهای مبتنی بر Chromium و Safari/iOS بارگذاری شود.
- {{domxref("HTMLIFrameElement.srcdoc")}}
  - : یک {{domxref("TrustedHTML")}} یا رشته که سند HTML بارگذاری‌شده در فریم را نمایش می‌دهد.
- {{domxref("HTMLIFrameElement.width")}}
  - : رشته‌ای که ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/iframe#width) را منعکس می‌کند و عرض فریم را نشان می‌دهد.

## روش‌های نمونه

_همچنین روش‌ها را از رابط والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLIFrameElement.getSVGDocument()")}}
  - : SVG جاسازی‌شده را به عنوان یک {{domxref("Document")}} برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("iframe")}}