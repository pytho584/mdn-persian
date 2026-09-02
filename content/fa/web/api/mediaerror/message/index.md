---
title: "MediaError: message property"
short-title: message
slug: Web/API/MediaError/message
page-type: web-api-instance-property
browser-compat: api.MediaError.message
---

{{APIRef("HTML DOM")}}

خاصیت فقط-خواندنی **`MediaError.message`** یک رشته‌ی قابل‌خواندن برای انسان برمی‌گرداند که جزئیات تشخیصی خاص مربوط به خطای توصیف‌شده توسط شیء `MediaError` را ارائه می‌دهد، یا اگر هیچ اطلاعات تشخیصی قابل تعیین یا ارائه نباشد، یک رشته‌ی خالی (`""`) برمی‌گرداند.

## مقدار

رشته‌ای که توضیحی دقیق و خاص از آنچه اشتباه رخ داده و احتمالاً چگونگی رفع آن ارائه می‌دهد. این یک توضیح عمومی از مقدار خاصیت {{domxref("MediaError.code")}} نیست، بلکه به عمق جزئیات این خطای خاص و شرایط آن می‌پردازد.
اگر جزئیات خاصی در دسترس نباشد، این رشته خالی است.

## مثال‌ها

### ثبت پیام‌های MediaError

این مثال یک عنصر {{HTMLElement("audio")}} ایجاد می‌کند، یک کنترل‌کننده خطا برای آن تنظیم می‌کند، سپس به کاربر اجازه می‌دهد با کلیک روی دکمه‌ها انتخاب کند که یک فایل صوتی معتبر یا یک فایل گمشده را به ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/audio#src) عنصر اختصاص دهد. کنترل‌کننده خطا، خطوط گزارش را در یک جعبه روی صفحه نمایش می‌دهد که خطا را توصیف می‌کند، شامل `code`، `message` و یک نکته که ممکن است برای بازدیدکنندگان مفیدتر از `message` تشخیصی باشد:

```html
<audio controls id="audio"></audio>
<div>
  <button id="valid-button">فایل معتبر</button>
  <button id="invalid-button">فایل گمشده</button>
  <button id="svg-button">فرمت اشتباه</button>
</div>
<pre id="log">گزارش‌ها:</pre>
```

```css hidden
pre {
  white-space: wrap;
  border: 1px solid grey;
}
```

این مثال یک عنصر {{HTMLElement("audio")}} ایجاد می‌کند و به کاربر اجازه می‌دهد یا یک فایل موسیقی معتبر به آن اختصاص دهد، یا یک پیوند به فایلی که وجود ندارد. این به ما امکان می‌دهد رفتار کنترل‌کننده رویداد {{domxref("HTMLMediaElement/error_event", "error")}} را ببینیم که توسط یک کنترل‌کننده رویداد که به خود عنصر `<audio>` اضافه می‌کنیم دریافت می‌شود.

ابتدا، شیء {{domxref("MediaError")}} توصیف‌کننده خطا را از خاصیت {{domxref("HTMLMediaElement.error", "error")}} روی {{domxref("HTMLAudioElement")}} که نمایانگر پخش‌کننده صدا است، دریافت می‌کند. سپس `code` عددی خطا با ثابت‌های `MediaError` که در ابتدا تعریف نشده‌اند، مقایسه می‌شود. اگر `err.code` برابر با هر ثابتی باشد، یک نکته عمومی با افزودن `MediaError.message` به خط گزارش برای ارائه اطلاعات تشخیصی دقیق‌تر برای توسعه‌دهندگان ایجاد می‌کند. متن حاصل به عنصر `<pre>` اضافه می‌شود:

```js
const audioElement = document.getElementById("audio");
const validButton = document.getElementById("valid-button");
const invalidButton = document.getElementById("invalid-button");
const svgButton = document.getElementById("svg-button");

const logMessage = (logLine) => {
  const now = new Date();
  const timestamp = now.toLocaleTimeString();
  document.getElementById("log").innerText += `\n[${timestamp}] ${logLine}`;
};

validButton.addEventListener("click", () => {
  audioElement.src = "https://mdn.github.io/shared-assets/audio/guitar.mp3";
});

svgButton.addEventListener("click", () => {
  audioElement.src =
    "https://mdn.github.io/shared-assets/images/examples/dino.svg";
});

invalidButton.addEventListener("click", () => {
  audioElement.src = "no-file-here.mp3";
});

audioElement.onerror = () => {
  const err = audioElement.error;
  let userHint = "";

  switch (err.code) {
    case MediaError.MEDIA_ERR_ABORTED:
      userHint = "پخش صدا لغو شد.";
      break;
    case MediaError.MEDIA_ERR_NETWORK:
      userHint = "یک خطای شبکه هنگام دریافت صدا رخ داد.";
      break;
    case MediaError.MEDIA_ERR_DECODE:
      userHint = "یک خطا هنگام رمزگشایی صدا رخ داد.";
      break;
    case MediaError.MEDIA_ERR_SRC_NOT_SUPPORTED:
      userHint = "صدا گمشده است یا فرمت پشتیبانی‌نشده‌ای دارد.";
      break;
    default:
      userHint += "یک خطای ناشناخته رخ داد.";
      break;
  }

  const message = err.message || "هیچ پیامی در دسترس نیست";

  logMessage(`کد خطا ${err.code} (${err.message})، ${userHint}`);
};
```

روی دکمه "فایل معتبر" کلیک کنید تا پخش طبق انتظار شروع شود، دکمه "فایل گمشده" برای تلاش برای بارگذاری یک منبع گمشده، و دکمه "فرمت اشتباه" برای تلاش برای تنظیم یک فایل SVG به عنوان منبع عنصر صوتی. مقایسه خروجی گزارش برای دو حالت خطا تفاوت بین `code` و `message` یک `MediaError` را نشان می‌دهد:

{{embedlivesample("logging_mediaerror_messages", , "300")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("MediaError")}}: واسطی که برای تعریف خاصیت `MediaError.message` استفاده می‌شود
- {{HTMLElement("audio")}}، {{HTMLElement("video")}}