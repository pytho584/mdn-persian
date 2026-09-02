---
title: "NavigateEvent: destination property"
short-title: destination
slug: Web/API/NavigateEvent/destination
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.destination
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`destination`** در رابط {{domxref("NavigateEvent")}} یک شیء {{domxref("NavigationDestination")}} برمی‌گرداند که مقصد مورد نظر برای ناوبری را نشان می‌دهد.

## مقدار

یک شیء {{domxref("NavigationDestination")}}.

## مثال‌ها

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

- [مسیریابی مدرن سمت کلاینت: رابط برنامه‌نویسی Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)