---
title: "HTMLMediaElement: getStartDate() method"
short-title: getStartDate()
slug: Web/API/HTMLMediaElement/getStartDate
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.getStartDate
---

{{APIRef("HTML DOM")}}

متد **`getStartDate()`** در رابط {{domxref("HTMLMediaElement")}} یک شیء جدید از نوع {{jsxref("Date")}} برمی‌گرداند که تاریخ و زمان واقعی (جهان واقعی) متناظر با شروع رسانه را نشان می‌دهد.

این متد برای جریان‌های رسانه‌ای که به یک ساعت واقعی متصل هستند (مانند پخش زنده‌ای که در یک تاریخ و زمان مشخص شروع شده است) مفید است. برای رسانه‌ای که حاوی اطلاعات تاریخ و زمان نیست، شیء `Date` برگشتی دارای مقدار زمانی {{jsxref("NaN")}} خواهد بود.

## نحو

```js-nolint
getStartDate()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Date")}} که تاریخ و زمان شروع رسانه را نشان می‌دهد. اگر رسانه حاوی اطلاعات تاریخ و زمان نباشد، شیء `Date` برگشتی دارای مقدار زمانی `NaN` خواهد بود.

## توضیحات

در داخل، هر عنصر رسانه یک تاریخ شروع را ردیابی می‌کند که در ابتدا `NaN` (تنظیم نشده) است. پس از اینکه مرورگر داده‌های کافی برای خواندن فراداده‌ی رسانه بارگذاری کرد، تاریخ شروع را به زمان واقعی که متناظر با شروع رسانه است تنظیم می‌کند – اگر قالب رسانه آن را فراهم کند. در غیر این صورت، تاریخ شروع `NaN` باقی می‌ماند.

برای رسانه‌ای که زمان و تاریخ شروع را مشخص می‌کند (مثلاً یک پخش زنده تلویزیونی که از طریق وب پخش می‌شود)، `getStartDate()` یک شیء `Date` متناظر با زمان واقعی شروع رسانه برمی‌گرداند. این امکان را فراهم می‌کند که کنترل‌های پخش‌کننده‌ی رسانه، زمان‌های مطلق (مانند «۲:۳۰ بعد از ظهر») را به جای زمان‌های نسبی به شروع پخش (مانند «۳ ساعت و ۱۲ دقیقه») نمایش دهند.

شیء `Date` برگشتی در هر یک از موارد زیر مقدار زمانی `NaN` خواهد داشت (که آن را به یک [تاریخ نامعتبر](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date) تبدیل می‌کند):

- هنوز داده‌ای بارگذاری نشده است ({{domxref("HTMLMediaElement.readyState", "readyState")}} برابر `HAVE_NOTHING` است)، بنابراین تاریخ شروع تنظیم نشده است.
- قالب رسانه شامل اطلاعات تاریخ و زمان نیست.

تاریخ شروع تضمین نمی‌شود که بلافاصله پس از رویداد {{domxref("HTMLMediaElement/loadedmetadata_event", "loadedmetadata")}} در دسترس باشد. برای مثال، جریان‌های [HLS](https://developer.apple.com/documentation/http-live-streaming) تاریخ‌ها را در برچسب‌های `#EXT-X-PROGRAM-DATE-TIME` در سطح سگمنت حمل می‌کنند، که ممکن است در آن نقطه هنوز خوانده نشده باشند. گوش دادن به رویداد {{domxref("HTMLMediaElement/loadeddata_event", "loadeddata")}} در عوض در میان قالب‌ها قابل اطمینان‌تر است، زیرا تا آن زمان مرورگر داده‌های کافی برای تعیین تاریخ شروع بارگذاری کرده است.

## مثال‌ها

### نمایش تاریخ شروع یک جریان زنده

این مثال تاریخ شروع یک جریان زنده را بازیابی می‌کند – تاریخ و زمان واقعی که پخش در آن شروع شده است، همانطور که توسط سرور در جریان تعبیه شده است – و آن را نمایش می‌دهد. به رویداد {{domxref("HTMLMediaElement/loadeddata_event", "loadeddata")}} گوش می‌دهد، که پس از بارگذاری داده‌های کافی برای در دسترس بودن تاریخ شروع، فعال می‌شود.

#### HTML

```html
<video src="livestream.m3u8" controls></video>
<output>تاریخ شروع: در حال بارگذاری…</output>
```

#### JavaScript

```js
const video = document.querySelector("video");
const display = document.querySelector("output");

video.addEventListener("loadeddata", () => {
  const startDate = video.getStartDate();

  if (isNaN(startDate.getTime())) {
    display.textContent = "تاریخ شروع: در دسترس نیست";
  } else {
    display.textContent = `تاریخ شروع: ${startDate.toLocaleString()}`;
  }
});
```

#### نتیجه

خروجی زیر تاریخ شروع رسانه را، همانطور که توسط سرور ارائه شده است، نشان می‌دهد.
توجه داشته باشید که این در فراداده‌های مثال موجود در [stream.m3u8](https://github.com/mdn/dom-examples/blob/main/media/getstartdate/stream.m3u8) رمزگذاری شده است.

{{EmbedGHLiveSample("dom-examples/media/getstartdate/", '100%', 400)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}
- {{domxref("HTMLMediaElement.currentTime")}}
- {{domxref("HTMLMediaElement.duration")}}