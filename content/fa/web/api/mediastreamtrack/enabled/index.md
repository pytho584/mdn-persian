---
title: "MediaStreamTrack: enabled property"
short-title: enabled
slug: Web/API/MediaStreamTrack/enabled
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.enabled
---

{{APIRef("Media Capture and Streams")}}

خاصیت **`enabled`** در رابط {{domxref("MediaStreamTrack")}} یک مقدار بولین است که اگر
`true` باشد یعنی مسیر (track) مجاز است جریان منبع را رندر کند و اگر
`false` باشد یعنی مجاز نیست. می‌توان از این خاصیت برای قطع عمدی صدای یک مسیر استفاده کرد.

وقتی یک مسیر فعال است، داده‌های آن از منبع به مقصد خروجی داده می‌شود؛
در غیر این صورت، فریم‌های خالی خروجی داده می‌شوند.

در مورد صدا، یک مسیر غیرفعال فریم‌های سکوت تولید می‌کند (یعنی فریم‌هایی که در آنها
مقدار هر نمونه ۰ است). برای مسیرهای ویدیو، هر فریم کاملاً با پیکسل‌های سیاه پر می‌شود.

مقدار `enabled`، در اصل، نشان‌دهنده چیزی است که یک کاربر معمولی آن را حالت قطع صدا برای یک مسیر در نظر می‌گیرد، در حالی که خاصیت {{domxref("MediaStreamTrack.muted", "muted")}}
وضعیتی را نشان می‌دهد که در آن مسیر به طور موقت قادر به خروجی داده نیست،
مانند سناریویی که فریم‌ها در حین انتقال از دست رفته‌اند.

> [!NOTE]
> اگر مسیر قطع شده باشد، مقدار این خاصیت
> قابل تغییر است، اما تأثیری نخواهد داشت.

## مقدار

وقتی `true` باشد، `enabled` نشان می‌دهد که مسیر مجاز است
رسانه واقعی خود را به خروجی رندر کند. وقتی `enabled` روی
`false` تنظیم شود، مسیر فقط فریم‌های خالی تولید می‌کند.

فریم‌های صوتی خالی مقدار هر نمونه را ۰ دارند. فریم‌های ویدیویی خالی هر پیکسل را سیاه دارند.

> [!NOTE]
> هنگام پیاده‌سازی ویژگی قطع/وصل صدا، باید از
> خاصیت `enabled` استفاده کنید.

## نکات استفاده

اگر {{domxref("MediaStreamTrack")}} نشان‌دهنده ورودی ویدیو از یک دوربین باشد،
غیرفعال کردن مسیر با تنظیم `enabled` به `false` همچنین
نشان‌دهنده‌های فعالیت دستگاه را به‌روز می‌کند تا نشان دهد دوربین در حال ضبط یا استریم نیست.
برای مثال، چراغ سبز «در حال استفاده» در کنار دوربین در رایانه‌های iMac و MacBook
در حالی که مسیر به این روش قطع است، خاموش می‌شود.

## مثال

این مثال یک کنترل‌کننده رویداد {{domxref("Element/click_event", "click")}} را برای یک دکمه توقف (pause) نشان می‌دهد.

```js
pauseButton.onclick = (evt) => {
  const newState = !myAudioTrack.enabled;

  pauseButton.innerHTML = newState ? "&#x25B6;&#xFE0F;" : "&#x23F8;&#xFE0F;";
  myAudioTrack.enabled = newState;
};
```

این یک متغیر به نام `newState` ایجاد می‌کند که معکوس مقدار فعلی
`enabled` است، سپس از آن برای انتخاب یا کاراکتر ایموجی «play» یا کاراکتر ایموجی «pause» به عنوان
{{domxref("Element.innerHTML", "innerHTML")}} جدید عنصر دکمه توقف استفاده می‌کند.

در نهایت، مقدار جدید `enabled` ذخیره می‌شود تا تغییر اعمال شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaStream")}}
- {{domxref("MediaStreamTrack")}}
- [WebRTC](/en-US/docs/Web/API/WebRTC_API)