---
title: NavigationActivation
slug: Web/API/NavigationActivation
page-type: web-api-interface
browser-compat: api.NavigationActivation
---

{{APIRef("Navigation API")}}

رابط **`NavigationActivation`** در [Navigation API](/en-US/docs/Web/API/Navigation_API)، نمایانگر یک پیمایش اخیر بین اسناد (cross-document) است. این رابط شامل نوع پیمایش و ورودی‌های تاریخچهٔ سند مبدأ و سند مقصد است.

به این شیء از طریق خصوصیت‌های {{domxref("PageSwapEvent.activation")}} و {{domxref("Navigation.activation")}} دسترسی پیدا می‌کنید. توجه داشته باشید که در هر مورد، `NavigationActivation` یک پیمایش متفاوت را نشان می‌دهد:

- `Navigation.activation` اطلاعات مربوط به پیمایش به صفحهٔ فعلی را نشان می‌دهد.
- `PageSwapEvent.activation` اطلاعات مربوط به پیمایش به صفحهٔ بعدی را نشان می‌دهد.

## خصوصیات نمونه

- {{domxref("NavigationActivation.entry", "entry")}} {{ReadOnlyInline}}
  - : شامل یک شیء {{domxref("NavigationHistoryEntry")}} است که ورودی تاریخچهٔ سند ورودی («به») را در این پیمایش نشان می‌دهد. این مقدار معادل خصوصیت {{domxref("Navigation.currentEntry")}} در لحظه‌ای است که سند ورودی فعال شده است.
- {{domxref("NavigationActivation.from", "from")}} {{ReadOnlyInline}}
  - : شامل یک شیء {{domxref("NavigationHistoryEntry")}} است که ورودی تاریخچهٔ سند خروجی («از») را در این پیمایش نشان می‌دهد.
- {{domxref("NavigationActivation.navigationType", "navigationType")}} {{ReadOnlyInline}}
  - : شامل رشته‌ای است که نوع پیمایش را مشخص می‌کند.

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
> برای مشاهدهٔ دموی زنده‌ای که این کد از آن گرفته شده است، [فهرست اعضای تیم Chrome DevRel](https://view-transitions.chrome.dev/profiles/mpa/) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Navigation API](/en-US/docs/Web/API/Navigation_API)
- [View Transition API](/en-US/docs/Web/API/View_Transition_API)