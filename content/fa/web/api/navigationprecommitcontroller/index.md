---
title: NavigationPrecommitController
slug: Web/API/NavigationPrecommitController
page-type: web-api-interface
browser-compat: api.NavigationPrecommitController
---

{{APIRef("Navigation API")}}

رابط **`NavigationPrecommitController`** از {{domxref("Navigation API", "Navigation API", "", "nocode")}} به عنوان آرگومان به یک callback [مدیر پیش‌تعـهد (precommit handler)](/en-US/docs/Web/API/NavigateEvent/intercept#precommithandler) ناوبری ارسال می‌شود.

این callback برای مدیریت هرگونه تغییر در ناوبری که قبل از commit (ثبت) شدن (و نمایش واقعی URL مقصد در مرورگر) لازم است، استفاده می‌شود، مانند لغو یا هدایت آن به جای دیگر در صورت نیاز.
این رابط (interface) روش‌هایی برای هدایت به یک URL جدید و به‌روزرسانی تاریخچه و state، و همچنین پیکربندی پویای رفتار ناوبری پس از commit فراهم می‌کند.

{{InheritanceDiagram}}

## روش‌های نمونه

- {{domxref("NavigationPrecommitController/addHandler", "addHandler()")}}
  - : یک تابع callback مدیریت‌گر (handler) اضافه می‌کند که پس از commit شدن ناوبری اجرا خواهد شد، انگار که با استفاده از آرگومان [`options.handler`](/en-US/docs/Web/API/NavigateEvent/intercept#handler) به {{domxref("NavigateEvent.intercept()")}} اضافه شده است.
- {{domxref("NavigationPrecommitController.redirect", "redirect()")}}
  - : مرورگر را به یک URL مشخص هدایت می‌کند و رفتار تاریخچه و هرگونه اطلاعات state دلخواه را مشخص می‌کند.

## توضیحات

هنگام مشخص کردن رفتار ناوبری درون‌سند (same-document) از طریق متد {{domxref("NavigateEvent.intercept()")}}، می‌توان اقدامات پیش‌تعـهد (precommit) ناوبری را از طریق callback [`precommitHandler`](/en-US/docs/Web/API/NavigateEvent/intercept#precommithandler) مشخص کرد. اقدامات پیش‌تعـهد برای تغییر یا لغو ناوبری در حال انجام، یا برای انجام کار در حین انجام ناوبری و قبل از commit آن استفاده می‌شوند (به [مثال اولیه ناوبری پیش‌تعـهد](#basic_precommit_navigation_example) مراجعه کنید).

برای مشخص کردن رفتار هدایت، از شیء `NavigationPrecommitController` که به تابع callback `precommitHandler` شما ارسال می‌شود استفاده می‌کنید. درون بدنه تابع، می‌توانید متد `NavigationPrecommitController.redirect()` را فراخوانی کنید که یک شیء حاوی URL هدایت، به علاوه هرگونه رفتار تاریخچه و اطلاعات state مورد نیاز را به عنوان آرگومان می‌پذیرد.

پس از commit شدن یک ناوبری، یک callback مدیریت‌گر پس از commit (post-commit handler) می‌تواند برای انجام عملیاتی مانند واکشی و رندر کردن محتوا اجرا شود. اگر کد ناوبری پس از commit به داده‌های جمع‌آوری شده در زمان اجرا در `precommitHandler` شما وابسته باشد، می‌توانید درون مدیریت‌گر پیش‌تعـهد خود، متد {{domxref("NavigationPrecommitController/addHandler", "addHandler()")}} را فراخوانی کنید تا این callback مدیریت‌گر پس از commit را به صورت پویا اضافه کنید. توجه داشته باشید که اگر کد پس از commit مستقل از کد پیش از commit باشد، می‌توانید به جای آن، callback [`handler`](/en-US/docs/Web/API/NavigateEvent/intercept#handler) را به متد {{domxref("NavigateEvent.intercept()")}} ارسال کنید.

برای زمینه بیشتر، به [توضیحات `intercept()`](/en-US/docs/Web/API/NavigateEvent/intercept#description) مراجعه کنید.

## مثال‌ها

### مثال اولیه ناوبری پیش‌تعـهد

قطعه کد زیر نشان می‌دهد که چگونه اگر کاربر به یک صفحه محدود شده برود و وارد سیستم نشده باشد، مرورگر را به یک صفحه ورود هدایت کنید.

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/restricted/") && !userSignedIn) {
    event.intercept({
      async precommitHandler(controller) {
        controller.redirect("/signin/", {
          state: "signin-redirect",
          history: "push",
        });
      },
    });
  }
});
```

این الگو ساده‌تر از جایگزین آن یعنی لغو ناوبری اصلی و شروع یک ناوبری جدید به مکان هدایت است، زیرا از نمایش حالت میانی جلوگیری می‌کند. به عنوان مثال، تنها یک رویداد {{domxref("Navigation.navigatesuccess_event", "navigatesuccess")}} یا {{domxref("Navigation.navigateerror_event", "navigateerror")}} فعال می‌شود، و اگر ناوبری توسط فراخوانی {{domxref("Navigation.navigate()")}} راه‌اندازی شده باشد، promise تنها زمانی تکمیل می‌شود که به مقصد هدایت رسیده باشید.

### اضافه کردن مدیریت‌گری که به رفتار پیش‌تعـهد وابسته است

این یک تغییر کوچک از مثال قبلی است که همچنین یک پیام به کاربر نشان می‌دهد که دلیل ورود به صفحه ورود پس از هدایت را توضیح می‌دهد. این کار از `addHandler()` در مدیریت‌گر پیش‌تعـهد برای اضافه کردن مدیریت‌گر پس از commit که پیام را نمایش می‌دهد استفاده می‌کند.

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/restricted/") && !userSignedIn) {
    event.intercept({
      async precommitHandler(controller) {
        controller.redirect("/signin/", {
          state: "signin-redirect",
          history: "push",
        });

        // از addHandler برای راه‌اندازی منطق پس از commit شدن صفحه /signin/ استفاده کنید
        controller.addHandler(() => {
          showMessage("لطفاً برای مشاهده آن محتوا وارد شوید.");
        });
      },
    });
  }
});
```

یکی از مزایای این رویکرد این است که مدیریت‌گر تنها در صورتی اجرا می‌شود که هدایت commit شود. اگر با ارسال [`options.handler`](/en-US/docs/Web/API/NavigateEvent/intercept) به `intercept()` اضافه می‌شد، مدیریت‌گر برای همه رویدادها اجرا می‌شد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)