---
title: "NavigationDestination: url property"
short-title: url
slug: Web/API/NavigationDestination/url
page-type: web-api-instance-property
browser-compat: api.NavigationDestination.url
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`url`** از رابط {{domxref("NavigationDestination")}}، نشانی اینترنتی (URL) مقصد ناوبری را برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

### مدیریت یک ناوبری با استفاده از `intercept()`

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)