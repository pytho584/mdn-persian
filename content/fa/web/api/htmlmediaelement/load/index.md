---
title: "HTMLMediaElement: load() method"
short-title: load()
slug: Web/API/HTMLMediaElement/load
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.load
---

{{APIRef("HTML DOM")}}

متود **`load()`** مربوط به {{domxref("HTMLMediaElement")}}، عنصر رسانه را به حالت اولیه خود بازنمی‌گرداند و فرآیند انتخاب منبع رسانه و بارگذاری رسانه را برای آماده‌سازی پخش از ابتدا آغاز می‌کند.

میزان داده‌های رسانه‌ای که از قبل دریافت می‌شود، با توجه به مقدار ویژگی [`preload`](/en-US/docs/Web/HTML/Reference/Elements/video#preload) عنصر تعیین می‌شود.

این متود معمولاً تنها زمانی مفید است که تغییرات پویایی در مجموعه منابع موجود برای عنصر رسانه ایجاد کرده‌اید، یا با تغییر ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/video#src) عنصر یا با افزودن یا حذف عناصر {{HTMLElement("source")}} که در داخل خود عنصر رسانه قرار دارند. `load()` عنصر را بازنشانی می‌کند و منابع موجود را دوباره اسکن می‌کند و در نتیجه تغییرات اعمال می‌شوند.

## Syntax

```js-nolint
load()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Usage notes

فراخوانی `load()` تمام عملیات در حال انجام مربوط به این عنصر رسانه را لغو می‌کند و سپس فرآیند انتخاب و بارگذاری یک منبع رسانه مناسب را با توجه به گزینه‌های مشخص‌شده در عنصر {{HTMLElement("audio")}} یا {{HTMLElement("video")}} و ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/video#src) یا عنصر(های) فرزند {{HTMLElement("source")}} آغاز می‌کند. این موضوع با جزئیات بیشتر در صفحه [ویدئو و صوتی HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio#using_multiple_source_formats_to_improve_compatibility) توضیح داده شده است.

فرآیند لغو هر فعالیت در حال انجام باعث می‌شود که هر {{jsxref("Promise")}} معلق برگردانده‌شده توسط {{domxref("HTMLMediaElement.play", "play()")}} بسته به وضعیت آن‌ها قبل از شروع بارگذاری رسانه جدید، fulfilled یا rejected شود. Promiseهای پخش معلق با یک {{domxref("DOMException")}} از نوع `"AbortError"` لغو می‌شوند.

همان‌طور که فرآیند بارگذاری پیش می‌رود، رویدادهای مناسب به خود عنصر رسانه ارسال می‌شوند:

- اگر عنصر از قبل در حال بارگذاری رسانه باشد، آن فرآیند بارگذاری لغو می‌شود و رویداد **{{domxref("HTMLMediaElement/abort_event", "abort")}}** ارسال می‌شود.
- اگر عنصر قبلاً با رسانه مقداردهی شده باشد، رویداد **{{domxref("HTMLMediaElement/emptied_event", "emptied")}}** ارسال می‌شود.
- اگر بازنشانی موقعیت پخش به ابتدای رسانه در واقع موقعیت پخش را تغییر دهد (یعنی از قبل در ابتدا نبوده باشد)، رویداد **{{domxref("HTMLMediaElement/timeupdate_event", "timeupdate")}}** ارسال می‌شود.
- پس از انتخاب رسانه و آماده‌شدن بارگذاری، رویداد **{{domxref("HTMLMediaElement/loadstart_event", "loadstart")}}** تحویل داده می‌شود.
- از این نقطه به بعد، رویدادها دقیقاً مانند هر بارگذاری رسانه‌ای ارسال می‌شوند.

## Examples

این مثال یک عنصر {{HTMLElement("video")}} را در سند پیدا می‌کند و با فراخوانی `load()` آن را بازنشانی می‌کند.

```js
const mediaElem = document.querySelector("video");
mediaElem.load();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}