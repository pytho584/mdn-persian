---
title: PageRevealEvent
slug: Web/API/PageRevealEvent
page-type: web-api-interface
browser-compat: api.PageRevealEvent
---

{{APIRef("HTML DOM")}}

شیء رویداد **`PageRevealEvent`** در داخل توابع مدیریت‌کنندهٔ رویداد {{domxref("Window.pagereveal_event", "pagereveal")}} در دسترس قرار می‌گیرد.

در یک پیمایش بین‌اسنادی (cross-document navigation)، این رویداد به شما امکان می‌دهد تا در سند مقصد، یک [view transition](/en-US/docs/Web/API/View_Transition_API) مرتبط را دستکاری کنید (با دسترسی به شیء {{domxref("ViewTransition")}} مربوطه)، مشروط بر اینکه پیمایش، view transition را فعال کرده باشد.

در خارج از view transitionها، این رویداد برای مواردی مانند اجرای انیمیشن شروع صفحه یا گزارش‌دهی بازدید صفحه نیز کاربرد دارد. این رویداد معادل اولین اجرای {{domxref("Window.requestAnimationFrame()")}} پس از پیمایش بین‌اسنادی است، به شرطی که `requestAnimationFrame()` را در {{htmlelement("head")}} سند فراخوانی کرده باشید. برای مثال، اگر تابع `reveal()` زیر را در `<head>` اجرا کنید:

```js
function reveal() {
  // Include startup animation here
}
/* This will fire in the first rendered frame after loading */
requestAnimationFrame(() => reveal());

/* This will fire if the page is restored from BFCache */
window.onpagehide = () => requestAnimationFrame(() => reveal());
```

## سازنده

- {{domxref("PageRevealEvent.PageRevealEvent", "PageRevealEvent()")}}
  - : یک نمونهٔ جدید از شیء `PageRevealEvent` می‌سازد.

## خصوصیات نمونه

- {{domxref("PageRevealEvent.viewTransition", "viewTransition")}} {{ReadOnlyInline}}
  - : شامل یک شیء {{domxref("ViewTransition")}} است که نمایانگر view transition فعال برای پیمایش بین‌اسنادی است.

## مثال‌ها

```js
window.addEventListener("pagereveal", async (e) => {
  // If the "from" history entry does not exist, return
  if (!navigation.activation.from) return;

  // Only run this if an active view transition exists
  if (e.viewTransition) {
    const fromUrl = new URL(navigation.activation.from.url);
    const currentUrl = new URL(navigation.activation.entry.url);

    // Went from profile page to homepage
    // ~> Set VT names on the relevant list item
    if (isProfilePage(fromUrl) && isHomePage(currentUrl)) {
      const profile = extractProfileNameFromUrl(fromUrl);

      // Set view-transition-name values on the elements to animate
      document.querySelector(`#${profile} span`).style.viewTransitionName =
        "name";
      document.querySelector(`#${profile} img`).style.viewTransitionName =
        "avatar";

      // Remove names after snapshots have been taken
      // so that we're ready for the next navigation
      await e.viewTransition.ready;
      document.querySelector(`#${profile} span`).style.viewTransitionName =
        "none";
      document.querySelector(`#${profile} img`).style.viewTransitionName =
        "none";
    }

    // Went to profile page
    // ~> Set VT names on the main title and image
    if (isProfilePage(currentUrl)) {
      // Set view-transition-name values on the elements to animate
      document.querySelector(`#detail main h1`).style.viewTransitionName =
        "name";
      document.querySelector(`#detail main img`).style.viewTransitionName =
        "avatar";

      // Remove names after snapshots have been taken
      // so that we're ready for the next navigation
      await e.viewTransition.ready;
      document.querySelector(`#detail main h1`).style.viewTransitionName =
        "none";
      document.querySelector(`#detail main img`).style.viewTransitionName =
        "none";
    }
  }
});
```

> [!NOTE]
> برای مشاهدهٔ نسخهٔ نمایشی زنده‌ای که این کد از آن گرفته شده است، به [فهرست اعضای تیم Chrome DevRel](https://view-transitions.chrome.dev/profiles/mpa/) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [View Transition API](/en-US/docs/Web/API/View_Transition_API)