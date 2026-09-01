---
title: "Communication with embedded frames"
---

---
title: Communication with embedded frames
slug: Web/API/Fenced_frame_API/Communication_with_embedded_frames
page-type: guide
---

{{DefaultAPISidebar("Fenced Frame API")}}

این مقاله توضیح می‌دهد که نحوهٔ برقراری ارتباط بین یک تعبیه‌کننده و محتوای تعبیه‌شده در انواع مختلف فریم (یعنی {{htmlelement("iframe")}} و {{htmlelement("fencedframe")}}) چگونه متفاوت است و داده‌های منتقل‌شده چگونه ذخیره می‌شوند.

## چگونه بین تعبیه‌کننده و یک `<iframe>` ارتباط برقرار کنیم

![نموداری که تفاوت بین ذخیره‌سازی محلی و ذخیره‌سازی مشترک و ارتباط با یک iframe را نشان می‌دهد، همان‌طور که در ادامه توضیح داده شده است](iframe-storage-communication.png)

هنگامی که کد شخص ثالث در یک `<iframe>` تعبیه می‌شود، `<iframe>` و تعبیه‌کننده می‌توانند آزادانه برای یکدیگر پیام ارسال کنند تا درخواست نوشتن داده در [ذخیره‌سازی مشترک](/en-US/docs/Web/API/Shared_Storage_API) سمت کلاینت خود را بدهند. تعبیه‌کننده می‌تواند از طریق یک کانال ارتباطی بین‌سندی و با استفاده از {{domxref("Window.postMessage()")}} به آن `<iframe>` درخواست دهد که داده‌ای را در ذخیره‌سازی شخص ثالث خودش بنویسد. شخص ثالث نیز می‌تواند درخواست‌های `postMessage()` را به تعبیه‌کننده ارسال کند.

از داخل `<iframe>` می‌توانید به رویداد [`message`](/en-US/docs/Web/API/Window/message_event) که از سمت تعبیه‌کننده می‌رسد گوش دهید. وقتی تعبیه‌کننده با استفاده از `postMessage()` پیامی به `<iframe>` ارسال می‌کند، `<iframe>` می‌تواند آن داده را دریافت کرده و در ذخیره‌سازی مشترک سمت کلاینت خودش ذخیره کند. برعکس، `<iframe>` نیز می‌تواند پیامی ارسال کند که تعبیه‌کننده به آن گوش دهد و با نوشتن داده در ذخیره‌سازی مشترک خود پاسخ دهد.

## چگونه بین تعبیه‌کننده و یک `<fencedframe>` ارتباط برقرار کنیم

فریم‌های حصاردار (Fenced frames) برای مواردی مانند نمایش تبلیغات هدفمندی در نظر گرفته شده‌اند که از طریق [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) و {{domxref("WindowSharedStorage.selectURL()")}} انتخاب می‌شوند. ارتباط بین `<fencedframe>`ها و سایر صفحاتِ خارج از `<fencedframe>` در همان صفحه، به‌طور عمدی محدود شده است؛ با این حال، یک روش ارتباط بین تعبیه‌کننده و worklet‌های ذخیره‌سازی مشترک وجود دارد: {{domxref("FencedFrameConfig.setSharedStorageContext()")}}.

> [!NOTE]
> در درون درختِ همان `<fencedframe>`، ارتباط بین فریم‌ها مجاز است. برای مثال، یک `<fencedframe>` ریشه می‌تواند به `<iframe>` فرزند در درخت خودش پیام بفرستد و یک `<iframe>` فرزند نیز می‌تواند به `<fencedframe>` والد پیام بفرستد.

بیایید به مثال پیچیده‌تری نگاه کنیم که از عملیات دروازه خروجی Select URL برای رندر کردن یک تبلیغ در یک `<fencedframe>` استفاده می‌کند.

![یک وضعیت تعبیه پیچیده که در آن یک تعبیه‌کننده یک iframe را تعبیه کرده، آن iframe یک fencedframe را تعبیه کرده، و آن fencedframe نیز یک iframe را تعبیه کرده است](multiple-embed-levels.png)

در این مثال، یک ناشر از یک ارائه‌دهنده محتوای شخص ثالث می‌خواهد محتوایی را در صفحه رندر کند. محتوایی که با {{domxref("WindowSharedStorage.selectURL()")}} انتخاب شده است در یک `<fencedframe>` رندر می‌شود و شامل یک `<iframe>` از یک ارائه‌دهنده اندازه‌گیری است. توجه داشته باشید که یک ناشر می‌تواند نمایانگر هر موجودیتی باشد که یک `<fencedframe>` شخص ثالث را تعبیه می‌کند. همچنین، یک ارائه‌دهنده اندازه‌گیری نمایانگر هر کد شخص ثالث تودرتویی است که درون `<fencedframe>` متعلق به شخص ثالثی دیگر اجرا می‌شود.

برای انتقال داده به یک `<fencedframe>` تا در worklet ذخیره‌سازی مشترک استفاده شود، تعبیه‌کننده می‌تواند داده را در یک {{domxref("FencedFrameConfig")}} قرار دهد. آن مقدار در داخل worklet ذخیره‌سازی مشترک به‌صورت {{domxref("WorkletSharedStorage.context")}} در دسترس خواهد بود. این داده در خارج از worklet در دسترس نیست و فقط در داخل محیط امن و خصوصی‌ای قابل دسترسی است که توسط یک worklet ذخیره‌سازی مشترک فراهم می‌شود.

![یک ناشر با استفاده از selectURL یک FencedFrameConfig ساخته است؛ این پیکربندی می‌تواند داده‌های زمینه‌ای را با setSharedStorageContext تنظیم کند که سپس در یک worklet ذخیره‌سازی مشترک در دسترس خواهد بود](share-contextual-data.png)

وقتی یک فراخوانی `selectURL()` یک `FencedFrameConfig` برمی‌گرداند، تعبیه‌کننده فریم می‌تواند با فراخوانی `setSharedStorageContext(data)` داده را به آن منتقل کند:

```js
const fencedFrameConfig = await window.sharedStorage.selectURL(
  "creative-rotation",
  urls,
  {
    // …
    resolveToConfig: true,
  },
);

fencedFrameConfig.setSharedStorageContext("some-data");

// Navigate the fenced frame to the config.
document.getElementById("my-fenced-frame").config = fencedFrameConfig;
```

باید `setSharedStorageContext(data)` را روی `fencedFrameConfig` فراخوانی کرد، پیش از آنکه ویژگی `config` عنصر `<fencedframe>` مقصد روی `fencedFrameConfig` تنظیم شود؛ زیرا این کار باعث ناوبری فریم می‌شود.

سپس در داخل یک worklet ذخیره‌سازی مشترک، می‌توان به `WorkletSharedStorage.context` دسترسی پیدا کرد تا داده بازیابی شود:

```js
class ReportingOperation {
  async run() {
    sharedStorage.set("some-data-from-embedder", sharedStorage.context);
  }
}
register("send-report", ReportingOperation);
```