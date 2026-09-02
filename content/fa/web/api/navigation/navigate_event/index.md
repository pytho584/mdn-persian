---
title: "Navigation: navigate event"
short-title: navigate
slug: Web/API/Navigation/navigate_event
page-type: web-api-event
browser-compat: api.Navigation.navigate_event
---

{{APIRef("Navigation API")}}

رویداد **`navigate`** از رابط {{domxref("Navigation")}} زمانی فعال می‌شود که [هر نوع ناوبری](https://github.com/WICG/navigation-api#appendix-types-of-navigations) آغاز شود و به شما امکان می‌دهد در صورت نیاز آن را رهگیری کنید.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("navigate", (event) => { })

onnavigate = (event) => { }
```

## Event type

یک {{domxref("NavigateEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("NavigateEvent")}}

## Examples

### Handling a navigation using `intercept()`

```js
navigation.addEventListener("navigate", (event) => {
  // Exit early if this navigation shouldn't be intercepted,
  // e.g. if the navigation is cross-origin, or a download request
  if (shouldNotIntercept(event)) {
    return;
  }

  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        // The URL has already changed, so show a placeholder while
        // fetching the new content, such as a spinner or loading page
        renderArticlePagePlaceholder();

        // Fetch the new content and display when ready
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);
      },
    });
  }
});
```

> [!NOTE]
> قبل از وجود Navigation API، برای انجام کاری مشابه باید به تمام رویدادهای کلیک روی لینک‌ها گوش می‌دادید، `event.preventDefault()` را اجرا می‌کردید، فراخوانی مناسب {{domxref("History.pushState()")}} را انجام می‌دادید، و سپس نمای صفحه را بر اساس URL جدید تنظیم می‌کردید. و این کار همه ناوبری‌ها را مدیریت نمی‌کرد — فقط کلیک‌های لینک که توسط کاربر آغاز شده‌اند.

### Handling scrolling using `scroll()`

در این مثال از رهگیری یک ناوبری، تابع `handler()` با واکشی و رندر کردن محتوای مقاله شروع می‌کند، اما سپس محتوای ثانویه‌ای را واکشی و رندر می‌کند. منطقی است که به محض در دسترس بودن محتوای اصلی مقاله، صفحه را به آن اسکرول کنید تا کاربر بتواند با آن تعامل داشته باشد، به جای اینکه منتظر بمانید تا محتوای ثانویه نیز رندر شود. برای رسیدن به این هدف، یک فراخوانی {{domxref("NavigateEvent.scroll", "scroll()")}} بین این دو اضافه کرده‌ایم.

```js
navigation.addEventListener("navigate", (event) => {
  if (shouldNotIntercept(navigateEvent)) {
    return;
  }
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);

        event.scroll();

        const secondaryContent = await getSecondaryContent(url.pathname);
        addSecondaryContent(secondaryContent);
      },
    });
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)