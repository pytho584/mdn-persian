---
title: "ARIA: alert role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: alert role"
short-title: alert
slug: Web/Accessibility/ARIA/Reference/Roles/alert_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#alert
sidebar: accessibilitysidebar
---

نقش `alert` برای اطلاعات مهم و معمولاً حساس به زمان است. `alert` نوعی از [`status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role) است که به‌عنوان یک ناحیه زنده (live region) اتمیک پردازش می‌شود.

## توضیحات

نقش `alert` برای انتقال یک پیام مهم و معمولاً حساس به زمان به کاربر استفاده می‌شود. وقتی این نقش به یک عنصر اضافه می‌شود، مرورگر یک رویداد هشدار دسترس‌پذیر (accessible alert event) به محصولات فناوری کمکی ارسال می‌کند که سپس می‌توانند کاربر را مطلع کنند.

نقش alert فقط باید برای اطلاعاتی استفاده شود که نیاز به توجه فوری کاربر دارند، مثلاً:

- مقدار نامعتبر در یک فیلد فرم وارد شده است
- نشست ورود کاربر در حال انقضا است
- اتصال به سرور قطع شده است و تغییرات محلی ذخیره نخواهند شد

نقش `alert` فقط باید برای محتوای متنی استفاده شود، نه عناصر تعاملی مانند لینک‌ها یا دکمه‌ها. عنصر دارای نقش `alert` نیازی به دریافت فوکوس ندارد، زیرا صفحه‌خوان‌ها (گفتاری یا بریل) به‌طور خودکار محتوای به‌روزشده را اعلام می‌کنند، صرف‌نظر از اینکه فوکوس صفحه‌کلید هنگام افزودن نقش کجاست.

نقش `alert` به گره‌ای که حاوی پیام هشدار است اضافه می‌شود، **نه** عنصری که باعث ایجاد هشدار می‌شود. هشدارها [مناطق زنده قطعی (assertive live regions)](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) هستند. تنظیم `role="alert"` معادل تنظیم [`aria-live="assertive"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) و [`aria-atomic="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) است. از آنجایی که این عناصر فوکوس نمی‌گیرند، نیازی به مدیریت فوکوس نیست و هیچ تعامل کاربری نباید مورد نیاز باشد.

> [!WARNING]
> به دلیل ماهیت مزاحم آن، نقش `alert` باید به‌ندرت و فقط در شرایطی که توجه فوری کاربر لازم است استفاده شود.

نقش [`alert`](https://w3c.github.io/aria/#alert) یکی از پنج نقش [منطقه زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) است. تغییرات پویا که کمتر فوری هستند باید از روش‌های ملایم‌تری استفاده کنند، مانند شامل کردن `aria-live="polite"` یا استفاده از نقش منطقه زنده دیگر مانند [`status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role). اگر انتظار می‌رود کاربر هشدار را ببندد، باید از نقش [`alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role) استفاده شود.

مهم‌ترین نکته درباره نقش `alert` این است که برای محتوایی است که به‌صورت پویا نمایش داده می‌شود، نه محتوایی که هنگام بارگذاری صفحه ظاهر می‌شود. این نقش برای موقعیت‌هایی عالی است که کاربر فرمی را پر می‌کند و جاوااسکریپت برای افزودن پیام خطا استفاده می‌شود — هشدار بلافاصله پیام را می‌خواند. نباید روی HTML که کاربر با آن تعامل نداشته است استفاده شود. مثلاً اگر صفحه‌ای با چندین هشدار قابل‌مشاهده که در سراسر آن پراکنده‌اند بارگذاری شود، نباید از نقش alert استفاده کرد، زیرا پیام‌ها به‌صورت پویا ایجاد نشده‌اند.

مانند سایر [مناطق زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)، هشدارها فقط زمانی اعلام می‌شوند که محتوای عنصر دارای `role="alert"` _به‌روزرسانی_ شود. اطمینان حاصل کنید که عنصر دارای نقش ابتدا در نشانه‌گذاری صفحه وجود دارد — این کار مرورگر و صفحه‌خوان را برای نظارت بر تغییرات عنصر «آماده» می‌کند. پس از آن، هر تغییری در محتوا اعلام خواهد شد. سعی نکنید به‌صورت پویا عنصری با `role="alert"` اضافه/ایجاد کنید که از قبل با پیام هشدار موردنظر شما پر شده است — این کار معمولاً منجر به اعلام _نمی‌شود_، زیرا تغییر محتوا رخ نداده است.

از آنجا که نقش `alert` هر محتوای تغییر یافته را می‌خواند، باید با احتیاط استفاده شود. هشدارها، بنا به تعریف، مختل‌کننده هستند. چند هشدار همزمان و هشدارهای غیرضروری تجربه کاربری بدی ایجاد می‌کنند.

## مثال‌ها

در ادامه نمونه‌های رایج هشدارها و نحوه پیاده‌سازی آن‌ها آورده شده است:

### مثال ۱: قابل مشاهده کردن محتوای از پیش آماده‌شده در عنصری با نقش alert

اگر محتوای _داخل_ عنصر دارای `role="alert"` ابتدا با CSS پنهان شده باشد، قابل مشاهده کردن آن باعث فعال شدن هشدار می‌شود. این بدان معناست که یک عنصر ظرف هشدار موجود را می‌توان چندین بار «استفاده مجدد» کرد.

```css
.hidden {
  display: none;
}
```

```html
<div id="expirationWarning" role="alert">
  <span class="hidden">نشست ورود شما در ۲ دقیقه دیگر منقضی می‌شود</span>
</div>
```

```js
// حذف کلاس 'hidden' محتوای داخل عنصر را قابل مشاهده می‌کند، که باعث می‌شود صفحه‌خوان هشدار را اعلام کند:
document
  .getElementById("expirationWarning")
  .firstChild.classList.remove("hidden");
```

### مثال ۲: تغییر پویای محتوای داخل عنصری با نقش alert

با استفاده از جاوااسکریپت، می‌توانید محتوای _داخل_ عنصر دارای `role="alert"` را به‌صورت پویا تغییر دهید. توجه داشته باشید که اگر نیاز به فعال کردن همان هشدار چندین بار داشته باشید (یعنی محتوایی که به‌صورت پویا درج می‌کنید همان قبلی باشد)، این معمولاً به‌عنوان تغییر تلقی نمی‌شود و منجر به اعلام _نمی‌شود_. به همین دلیل، معمولاً بهتر است ابتدا محتوای ظرف هشدار را به‌طور خلاصه «پاک» کنید و سپس پیام هشدار را تزریق کنید.

```html
<div id="alertContainer" role="alert"></div>
```

```js
// پاک کردن محتوای ظرف
document.getElementById("alertContainer").textContent = "";
// تزریق پیام هشدار جدید
document.getElementById("alertContainer").textContent =
  `نشست شما در ${expiration} دقیقه دیگر منقضی می‌شود`;
```

### مثال ۳: ظرف هشدار پنهان بصری برای اعلان‌های صفحه‌خوان

امکان پنهان کردن بصری خود ظرف هشدار و استفاده از آن برای ارائه به‌روزرسانی‌ها/اعلان‌ها به‌طور خاص برای صفحه‌خوان‌ها وجود دارد. این می‌تواند در موقعیت‌هایی مفید باشد که محتوای مهم صفحه به‌روزرسانی شده است، اما تغییر بلافاصله برای کاربر صفحه‌خوان قابل توجه نباشد.

با این حال، مطمئن شوید که ظرف با `display:none` پنهان نشده است، زیرا این کار آن را حتی از فناوری‌های کمکی نیز پنهان می‌کند و در نتیجه از تغییرات مطلع نخواهند شد. به جای آن، از چیزی مانند [استایل‌های `.visually-hidden`](https://www.a11yproject.com/posts/how-to-hide-content/) استفاده کنید.

```html
<div id="hiddenAlertContainer" role="alert" class="visually-hidden"></div>
```

```css
.visually-hidden {
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
```

```js
// پاک کردن محتوای ظرف
document.getElementById("hiddenAlertContainer").textContent = "";
// تزریق پیام هشدار جدید
document.getElementById("hiddenAlertContainer").textContent =
  "همه موارد از موجودی شما حذف شدند.";
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
- [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic)
- [نقش ARIA: `log`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)
- [نقش ARIA: `marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role)
- [نقش ARIA: `status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)
- [نقش ARIA: `timer`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/timer_role)
- [نقش ARIA: `alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role)
- [ARIA: مناطق زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)
- [پشتیبانی از هشدار ARIA - Vispero](https://vispero.com/resources/aria-alert-support/)
- [مثال هشدار در شیوه‌های ARIA](https://www.w3.org/WAI/ARIA/apg/patterns/alert/examples/alert/)