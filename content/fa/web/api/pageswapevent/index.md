---
title: "PageSwapEvent"
slug: Web/API/PageSwapEvent
page-type: web-api-interface
browser-compat: api.PageSwapEvent
---

{{APIRef("HTML DOM")}}

شیء رویداد **`PageSwapEvent`** درون توابع کنترل‌کننده رویداد {{domxref("Window.pageswap_event", "pageswap")}} در دسترس قرار می‌گیرد.

رویداد `pageswap` زمانی فعال می‌شود که در حال پیمایش بین سندها هستید، درست زمانی که سند قبلی در آستانه تخلیه (unload) شدن است. در طول یک پیمایش بین سندی، شیء رویداد `PageSwapEvent` به شما امکان می‌دهد تا [انتقال نمای (view transition)](/en-US/docs/Web/API/View_Transition_API) مرتبط را از سندی که در حال پیمایش _از_ آن هستید، دستکاری کنید (دسترسی به شیء {{domxref("ViewTransition")}} مربوطه را فراهم می‌کند)، در صورتی که یک انتقال نمای توسط پیمایش آغاز شده باشد. همچنین دسترسی به اطلاعاتی درباره نوع پیمایش و سندهای جاری و مقصد را فراهم می‌کند.

## سازنده (Constructor)

- {{domxref("PageSwapEvent.PageSwapEvent", "PageSwapEvent()")}}
  - : یک نمونه جدید از شیء `PageSwapEvent` ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("PageSwapEvent.activation", "activation")}} {{ReadOnlyInline}}
  - : شامل یک شیء {{domxref("NavigationActivation")}} است که شامل نوع پیمایش و ورودی‌های تاریخچه سند جاری و مقصد برای یک پیمایش هم‌ریشه (same-origin) می‌باشد. اگر پیمایش دارای یک URL با منشأ متفاوت (cross-origin) در هر نقطه از زنجیره تغییرمسیر باشد، `null` برمی‌گرداند.
- {{domxref("PageSwapEvent.viewTransition", "viewTransition")}} {{ReadOnlyInline}}
  - : شامل یک شیء {{domxref("ViewTransition")}} است که نمایانگر انتقال نمای فعال برای پیمایش بین سندی است.

## مثال‌ها

```js
window.addEventListener("pageswap", async (e) => {
  // Only run this if an active view transition exists
  if (e.viewTransition) {
    const currentUrl = e.activation.from?.url
      ? new URL(e.activation.from.url)
      : null;
    const targetUrl = new URL(e.activation.entry.url);

    // Going from profile page to homepage
    // ~> The big img and title are the ones!
    if (isProfilePage(currentUrl) && isHomePage(targetUrl)) {
      // Set view-transition-name values on the elements to animate
      document.querySelector(`#detail main h1`).style.viewTransitionName =
        "name";
      document.querySelector(`#detail main img`).style.viewTransitionName =
        "avatar";

      // Remove view-transition-names after snapshots have been taken
      // Stops naming conflicts resulting from the page state persisting in BFCache
      await e.viewTransition.finished;
      document.querySelector(`#detail main h1`).style.viewTransitionName =
        "none";
      document.querySelector(`#detail main img`).style.viewTransitionName =
        "none";
    }

    // Going to profile page
    // ~> The clicked items are the ones!
    if (isProfilePage(targetUrl)) {
      const profile = extractProfileNameFromUrl(targetUrl);

      // Set view-transition-name values on the elements to animate
      document.querySelector(`#${profile} span`).style.viewTransitionName =
        "name";
      document.querySelector(`#${profile} img`).style.viewTransitionName =
        "avatar";

      // Remove view-transition-names after snapshots have been taken
      // Stops naming conflicts resulting from the page state persisting in BFCache
      await e.viewTransition.finished;
      document.querySelector(`#${profile} span`).style.viewTransitionName =
        "none";
      document.querySelector(`#${profile} img`).style.viewTransitionName =
        "none";
    }
  }
});
```

> [!NOTE]
> برای نسخه نمایشی زنده که این کد از آن گرفته شده است، به [فهرست اعضای تیم Chrome DevRel](https://view-transitions.chrome.dev/profiles/mpa/) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("View_Transition_API", "View Transition API")}}