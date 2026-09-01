---
title: "HTMLMediaElement: error property"
short-title: error
slug: Web/API/HTMLMediaElement/error
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.error
---

{{APIRef("HTML DOM")}}

خصوصیت **`HTMLMediaElement.error`** یک شیء {{domxref("MediaError")}} برای آخرین خطای رخ‌داده است، یا اگر خطایی رخ نداده باشد، مقدار `null` دارد. وقتی عنصر یک رویداد {{domxref("HTMLMediaElement/error_event", "error")}} دریافت می‌کند، می‌توانید با بررسی این شیء، جزئیات رویداد رخ‌داده را تعیین کنید.

## مقدار

یک شیء {{domxref("MediaError")}} که آخرین خطای رخ‌داده در عنصر رسانه‌ای را توصیف می‌کند، یا اگر خطایی رخ نداده باشد، `null`.

## مثال‌ها

این مثال یک عنصر ویدیو ایجاد می‌کند و یک مدیریت‌کننده خطا به آن اضافه می‌کند؛ مدیریت‌کننده خطا جزئیات را در کنسول ثبت می‌کند.

```js
const videoElement = document.createElement("video");
videoElement.onerror = () => {
  console.error(
    `Error ${videoElement.error.code}; details: ${videoElement.error.message}`,
  );
};
videoElement.src = "https://example.com/bogusvideo.mp4";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: واسطی که برای تعریف ویژگی `HTMLMediaElement.error` استفاده می‌شود
- {{HTMLElement("audio")}} و {{HTMLElement("video")}}