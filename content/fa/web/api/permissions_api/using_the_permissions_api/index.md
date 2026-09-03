---
title: Using the Permissions API
slug: Web/API/Permissions_API/Using_the_Permissions_API
page-type: guide
---

{{DefaultAPISidebar("Permissions API")}}

این مقاله راهنمای مقدماتی استفاده از [Permissions API](/en-US/docs/Web/API/Permissions_API) است؛ API‌ای که روش برنامه‌نویسی‌شده‌ای برای بررسی وضعیت مجوزهای APIِ مرتبط با بافتار کنونی فراهم می‌کند.

## دردسرِ درخواست مجوز…

مجوزها در وب یک «شرّ لازم» هستند؛ اما برای توسعه‌دهندگان، سروکار داشتن با آن‌ها چندان خوشایند نیست.

از نظر تاریخی، APIهای مختلف هرکدام رفتار ناسازگاری با مجوزهای خود داشتند؛ برای مثال، [Notifications API](/en-US/docs/Web/API/Notifications_API) متدهای مخصوص خود را برای بررسی وضعیت مجوز و درخواست مجوز داشت، در حالی که [Geolocation API](/en-US/docs/Web/API/Geolocation_API) چنین نبود.

[Permissions API](/en-US/docs/Web/API/Permissions_API) رویکردی یکپارچه برای توسعه‌دهندگان فراهم می‌کند و به آن‌ها اجازه می‌دهد تا در زمینهٔ مجوزها، تجربهٔ کاربری بهتری پیاده‌سازی کنند. به‌طور مشخص، توسعه‌دهندگان می‌توانند از {{domxref("Permissions.query()")}} برای بررسی اینکه آیا مجوز استفاده از یک API خاص در بافتار کنونی «اعطا شده» (granted)، «رد شده» (denied) یا نیازمند اجازهٔ صریح کاربر از طریق یک اعلان (prompt) است استفاده کنند. پرس‌وجوی مجوزها در رشتهٔ اصلی (main thread) به‌طور گسترده پشتیبانی می‌شود؛ همچنین در [Workers](/en-US/docs/Web/API/Permissions_API#api.workernavigator.permissions) نیز (با یک استثنای قابل توجه) پشتیبانی می‌شود.

بسیاری از APIها امروزه امکان پرس‌وجوی مجوز را فراهم می‌کنند؛ از جمله [Clipboard API](/en-US/docs/Web/API/Clipboard_API)، [Notifications API](/en-US/docs/Web/API/Notifications_API)، [Push API](/en-US/docs/Web/API/Push_API) و [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API). فهرستی از این APIها در [مرور API](/en-US/docs/Web/API/Permissions_API#permission-aware_apis) آمده است و می‌توانید وضعیت پشتیبانی مرورگرها را در [جدول سازگاری اینجا](/en-US/docs/Web/API/Permissions_API#api.permissions) ببینید.

{{domxref("Permissions")}} همچنین متدهای دیگری دارد که مخصوصاً برای درخواست مجوز استفاده از یک API یا لغو مجوز به کار می‌روند؛ اما این متدها منسوخ شده‌اند (غیراستاندارد هستند و/یا پشتیبانی گسترده‌ای ندارند).

## یک مثال ساده

برای این مقاله، یک دموی ساده به نام Location Finder آماده کرده‌ایم. این دمو با استفاده از موقعیت جغرافیایی (Geolocation)، موقعیت کنونی کاربر را دریافت و روی نقشهٔ Google نمایش می‌دهد:

![تصویری که نقشه‌ای از گرینفیلد، بریتانیا را نشان می‌دهد](location-finder-with-permissions-api.png)

می‌توانید [مثال را به‌صورت زنده اجرا کنید](https://chrisdavidmills.github.io/location-finder-permissions-api/) یا [کد منبع را در GitHub ببینید](https://github.com/chrisdavidmills/location-finder-permissions-api/tree/gh-pages). بیشتر کدها ساده و معمولی هستند؛ در ادامه فقط به بخش‌های مرتبط با Permissions API می‌پردازیم. اگر قصد مطالعهٔ بخش‌های دیگر را دارید، می‌توانید خودتان کد را بررسی کنید.

### دسترسی به Permissions API

ویژگی {{domxref("Navigator.permissions")}} به مرورگر اضافه شده تا دسترسی به شیء سراسری {{domxref("Permissions")}} ممکن شود. انتظار می‌رود این شیء در نهایت متدهایی برای پرس‌وجو، درخواست و لغو مجوزها داشته باشد؛ اگرچه در حال حاضر فقط شامل {{domxref("Permissions.query()")}} است؛ در ادامه ببینید.

### بررسی وضعیت مجوز

در مثال ما، کارکرد مجوزها در یک تابع به نام `handlePermission()` مدیریت می‌شود. این تابع ابتدا وضعیت مجوز را با استفاده از {{domxref("Permissions.query()")}} بررسی می‌کند. سپس بسته به مقدار ویژگی {{domxref("PermissionStatus.state", "state")}} از شیء {{domxref("PermissionStatus")}} که پس از resolve شدن Promise بازگردانده می‌شود، واکنش متفاوتی نشان می‌دهد:

- `"granted"`
  - : دکمهٔ «Enable Geolocation» پنهان می‌شود، زیرا اگر موقعیت جغرافیایی از قبل فعال باشد، این دکمه لازم نیست.
- `"prompt"`
  - : دکمهٔ «Enable Geolocation» پنهان می‌شود، زیرا اگر قرار باشد برای اعطای مجوزِ موقعیت جغرافیایی از کاربر پرسیده شود، این دکمه لازم نیست. سپس تابع {{domxref("Geolocation.getCurrentPosition()")}} اجرا می‌شود و از کاربر اجازه می‌خواهد؛ اگر اجازه داده شود، تابع `revealPosition()` اجرا می‌شود (که نقشه را نشان می‌دهد) و اگر اجازه رد شود، تابع `positionDenied()` اجرا می‌شود (که باعث ظاهرشدن دکمهٔ «Enable Geolocation» می‌شود).
- `"denied"`
  - : دکمهٔ «Enable Geolocation» نمایش داده می‌شود (این کد باید اینجا نیز وجود داشته باشد؛ برای زمانی که هنگام بارگذاری اولیهٔ صفحه، وضعیت مجوز این خاستگاه از ابتدا روی «denied» تنظیم شده باشد).

```js
function handlePermission() {
  navigator.permissions.query({ name: "geolocation" }).then((result) => {
    if (result.state === "granted") {
      report(result.state);
      geoBtn.style.display = "none";
    } else if (result.state === "prompt") {
      report(result.state);
      geoBtn.style.display = "none";
      navigator.geolocation.getCurrentPosition(
        revealPosition,
        positionDenied,
        geoSettings,
      );
    } else if (result.state === "denied") {
      report(result.state);
      geoBtn.style.display = "inline";
    }
    result.addEventListener("change", () => {
      report(result.state);
    });
  });
}

function report(state) {
  console.log(`Permission ${state}`);
}

handlePermission();
```

### توصیف‌گرهای مجوز

متد {{domxref("Permissions.query()")}} یک دیکشنری `PermissionDescriptor` را به‌عنوان پارامتر می‌پذیرد که شامل نام API موردنظر شماست. برخی APIها دارای `PermissionDescriptor`های پیچیده‌تری هستند که اطلاعات اضافی را حمل می‌کنند و از `PermissionDescriptor` پیش‌فرض ارث می‌برند. برای نمونه، `PushPermissionDescriptor` باید یک مقدار بولین نیز داشته باشد که مشخص می‌کند [`userVisibleOnly`](/en-US/docs/Web/API/PushManager/subscribe#parameters) برابر `true` است یا `false`.

### واکنش به تغییرات وضعیت مجوز

حتماً توجه کرده‌اید که در کد بالا به رویداد {{domxref("PermissionStatus.change_event", "change")}} متصل به شیء {{domxref("PermissionStatus")}} گوش می‌دهیم؛ این کار به ما امکان می‌دهد به هر تغییری در وضعیت مجوزِ API موردنظر واکنش نشان دهیم. در حال حاضر فقط تغییر وضعیت را گزارش می‌کنیم.