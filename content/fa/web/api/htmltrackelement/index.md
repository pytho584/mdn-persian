---
title: HTMLTrackElement
slug: Web/API/HTMLTrackElement
page-type: web-api-interface
browser-compat: api.HTMLTrackElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLTrackElement`** یک عنصر {{Glossary("HTML")}} از نوع {{HTMLElement("track")}} را درون {{Glossary("DOM")}} نمایش می‌دهد. این عنصر می‌تواند به‌عنوان فرزند {{HTMLElement("audio")}} یا {{HTMLElement("video")}} استفاده شود تا یک مسیر متنی (text track) حاوی اطلاعاتی مانند زیرنویس بسته (closed captions) یا زیرنویس (subtitles) را مشخص کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLTrackElement.kind")}}
  - : رشته‌ای که ویژگی HTML [`kind`](/en-US/docs/Web/HTML/Reference/Elements/track#kind) را منعکس می‌کند و نشان می‌دهد که مسیر متنی قرار است چگونه استفاده شود. مقادیر ممکن عبارت‌اند از: `subtitles`، `captions`، `descriptions`، `chapters` یا `metadata`.
- {{domxref("HTMLTrackElement.src")}}
  - : رشته‌ای که ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/track#src) را منعکس می‌کند و آدرس داده‌های مسیر متنی را نشان می‌دهد.
- {{domxref("HTMLTrackElement.srclang")}}
  - : رشته‌ای که ویژگی HTML [`srclang`](/en-US/docs/Web/HTML/Reference/Elements/track#srclang) را منعکس می‌کند و زبان داده‌های مسیر متنی را نشان می‌دهد.
- {{domxref("HTMLTrackElement.label")}}
  - : رشته‌ای که ویژگی HTML [`label`](/en-US/docs/Web/HTML/Reference/Elements/track#label) را منعکس می‌کند و عنوان قابل‌خواندن برای کاربرِ مسیر را نشان می‌دهد.
- {{domxref("HTMLTrackElement.default")}}
  - : یک مقدار بولی که ویژگی [`default`](/en-US/docs/Web/HTML/Reference/Elements/track#default) را منعکس می‌کند و نشان می‌دهد که اگر ترجیحات کاربر نشان ندهد که مسیر دیگری مناسب‌تر است، این مسیر فعال شود.
- {{domxref("HTMLTrackElement.readyState")}} {{ReadOnlyInline}}
  - : یک `unsigned short` برمی‌گرداند که وضعیت آمادگی مسیر را نشان می‌دهد:

    | Constant  | Value | توضیحات                                                                                                                                                                                                                                 |
    | --------- | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `NONE`    | 0     | نشان می‌دهد که نشانه‌های (cues) مسیر متنی دریافت نشده‌اند.                                                                                                                                                                               |
    | `LOADING` | 1     | نشان می‌دهد که مسیر متنی در حال بارگذاری است و تاکنون هیچ خطای مهلکی رخ نداده است. ممکن است نشانه‌های بیشتری توسط تجزیه‌گر به مسیر اضافه شوند.                                                                                           |
    | `LOADED`  | 2     | نشان می‌دهد که مسیر متنی بدون هیچ خطای مهلکی بارگذاری شده است.                                                                                                                                                                          |
    | `ERROR`   | 3     | نشان می‌دهد که مسیر متنی فعال بوده، اما وقتی عامل کاربر (user agent) تلاش کرد آن را دریافت کند، این کار به نحوی شکست خورده است. احتمالاً برخی یا همه نشانه‌ها وجود ندارند و دریافت نخواهند شد.                                             |

- {{domxref("HTMLTrackElement.track")}} {{ReadOnlyInline}}
  - : داده‌های مسیر متنی عنصر track را به‌صورت {{Domxref("TextTrack")}} برمی‌گرداند.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

## رویدادها

_رویدادها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

برای گوش دادن به این رویدادها از {{domxref("EventTarget/addEventListener", "addEventListener()")}} استفاده کنید یا یک شنونده رویداد را به ویژگی `oneventname` این رابط نسبت دهید:

- {{domxref("HTMLTrackElement.cuechange_event", "cuechange")}}
  - : زمانی ارسال می‌شود که {{domxref("TextTrack")}} زیربنایی، نشانه‌های ارائه‌شده در حال حاضر را تغییر دهد. این رویداد همیشه به `TextTrack` ارسال می‌شود، اما اگر یک `HTMLTrackElement` با مسیر مرتبط باشد، _همچنین_ به آن نیز ارسال می‌شود.
    همچنین می‌توانید از مدیریت‌کننده رویداد `oncuechange` برای ایجاد یک مدیریت‌کننده برای این رویداد استفاده کنید.

## نکات استفاده

### بارگذاری منبع متنی مسیر

داده‌های WebVTT یا TTML که نشانه‌های واقعی مسیر متنی را توصیف می‌کنند، اگر {{domxref("TextTrack.mode", "mode")}} مسیر در ابتدا در وضعیت `disabled` باشد، بارگذاری نمی‌شوند. اگر نیاز دارید پس از راه‌اندازی `<track>` بتوانید پردازشی روی مسیر انجام دهید، باید اطمینان حاصل کنید که `mode` مسیر یا `hidden` است (اگر نمی‌خواهید در ابتدا به کاربر ارائه شود) یا `showing` (برای نمایش اولیه مسیر). سپس می‌توانید بعداً حالت را مطابق میل خود تغییر دهید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML پیاده‌ساز این رابط: {{ HTMLElement("track") }}.