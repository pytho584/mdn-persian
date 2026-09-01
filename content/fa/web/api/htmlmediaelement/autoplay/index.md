---
title: "HTMLMediaElement: autoplay property"
short-title: autoplay
slug: Web/API/HTMLMediaElement/autoplay
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.autoplay
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.autoplay`** منعکس‌کنندهٔ ویژگی HTML [`autoplay`](/en-US/docs/Web/HTML/Reference/Elements/video#autoplay) است که نشان می‌دهد آیا پخش باید به‌محض در دسترس بودن رسانه‌ی کافی برای انجام آن بدون وقفه، به‌طور خودکار آغاز شود یا خیر.

یک عنصر رسانه‌ای که منبع آن یک {{domxref("MediaStream")}} است و ویژگی `autoplay` آن `true` باشد، هنگامی که فعال شود (یعنی زمانی که {{domxref("MediaStream.active")}} به `true` تبدیل شود)، پخش را آغاز خواهد کرد.

> [!NOTE]
> سایت‌هایی که به‌طور خودکار صدا (یا ویدئوهای دارای مسیر صوتی) را پخش می‌کنند، می‌توانند تجربه‌ای ناخوشایند برای کاربران باشند، بنابراین در صورت امکان باید از آن خودداری کرد. اگر مجبور به ارائه قابلیت پخش خودکار هستید، باید آن را به‌صورت انتخابی (opt-in) قرار دهید (یعنی کاربر باید به‌طور خاص آن را فعال کند). با این حال، پخش خودکار می‌تواند هنگام ایجاد عناصر رسانه‌ای که منبع آن‌ها بعداً و تحت کنترل کاربر تنظیم می‌شود، مفید باشد.

برای بررسی عمیق‌تر پخش خودکار، مسدودسازی پخش خودکار و نحوه واکنش زمانی که پخش خودکار توسط مرورگر کاربر مسدود می‌شود، مقالهٔ [راهنمای پخش خودکار برای رسانه و APIهای Web Audio](/en-US/docs/Web/Media/Guides/Autoplay) را ببینید.

## مقدار

یک مقدار بولی که اگر عنصر رسانه به‌محض بارگذاری محتوای کافی برای انجام پخش بدون وقفه، پخش را آغاز کند، `true` است.

> [!NOTE]
> برخی مرورگرها به کاربران امکان بازنویسی (override) `autoplay` را می‌دهند تا از پخش صدا یا ویدئوی مزاحم بدون اجازه یا در پس‌زمینه جلوگیری کنند. به شروع واقعی پخش توسط `autoplay` اعتماد نکنید و به جای آن از رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} استفاده کنید.

## نمونه‌ها

```html
<video id="video" controls>
  <source
    src="https://player.vimeo.com/external/250688977.sd.mp4?s=d14b1f1a971dde13c79d6e436b88a6a928dfe26b&profile_id=165" />
</video>
```

```js
// غیرفعال کردن پخش خودکار (توصیه می‌شود)
// false مقدار پیش‌فرض است
document.querySelector("#video").autoplay = false;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابط (interface) مورد استفاده برای تعریف ویژگی `HTMLMediaElement.autoplay`
- {{HTMLElement("audio")}}، {{HTMLElement("video")}}