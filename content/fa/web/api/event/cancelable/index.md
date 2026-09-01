---
title: "Event: cancelable property"
short-title: cancelable
slug: Web/API/Event/cancelable
page-type: web-api-instance-property
browser-compat: api.Event.cancelable
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`cancelable`** در رابط {{domxref("Event")}} نشان می‌دهد که آیا رویداد قابل لغو است یا نه؛ به این معنا که می‌توان از وقوع آن جلوگیری کرد، گویی هرگز رخ نداده است.

اگر رویداد قابل لغو _نباشد_، مقدار ویژگی `cancelable` آن `false` خواهد بود و شنونده رویداد نمی‌تواند از وقوع آن جلوگیری کند.

بیشتر رویدادهای بومی مرورگر که قابل لغو هستند، آن‌هایی هستند که در نتیجه تعامل کاربر با صفحه رخ می‌دهند. لغو رویدادهای {{domxref("Element/click_event", "click")}}، {{domxref("Element/wheel_event", "wheel")}} یا {{domxref("Window/beforeunload_event", "beforeunload")}} به ترتیب از کلیک کردن کاربر روی چیزی، اسکرول کردن صفحه با چرخ ماوس، یا خروج از صفحه جلوگیری می‌کند.

[رویدادهای مصنوعی](/en-US/docs/Web/API/Event/Event) ساخته‌شده توسط کد جاوااسکریپت دیگر، هنگام ساخت مشخص می‌کنند که آیا قابل لغو هستند یا نه.

برای لغو یک رویداد، متد {{domxref("event.preventDefault", "preventDefault()")}} را روی آن رویداد فراخوانی کنید. این کار از اجرای اقدام پیش‌فرض مرتبط با رویداد توسط پیاده‌سازی جلوگیری می‌کند.

شنونده‌های رویدادی که با انواع مختلفی از رویدادها سروکار دارند ممکن است بخواهند قبل از فراخوانی متدهای {{domxref("event.preventDefault", "preventDefault()")}} خود، مقدار `cancelable` را بررسی کنند.

## مقدار

یک مقدار بولی که اگر رویداد قابل لغو باشد، `true` است.

## مثال

برای مثال، تولیدکنندگان مرورگر پیشنهاد کرده‌اند که رویداد {{domxref("Element/wheel_event", "wheel")}} فقط [در اولین باری که شنونده فراخوانی می‌شود](https://github.com/WICG/interventions/issues/33) قابل لغو باشد — هر رویداد `wheel` بعدی قابل لغو نیست.

```js
function preventScrollWheel(event) {
  if (typeof event.cancelable !== "boolean" || event.cancelable) {
    // رویداد قابل لغو است، پس آن را لغو می‌کنیم.
    event.preventDefault();
  } else {
    // رویداد قابل لغو نیست، بنابراین فراخوانی preventDefault() روی آن ایمن نیست.
    console.warn(`رویداد زیر قابل لغو نبود:`);
    console.dir(event);
  }
}

document.addEventListener("wheel", preventScrollWheel);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}