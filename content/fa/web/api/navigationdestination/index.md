```markdown
---
title: "NavigationDestination"
---

---
title: NavigationDestination
slug: Web/API/NavigationDestination
page-type: web-api-interface
browser-compat: api.NavigationDestination
---

{{APIRef("Navigation API")}}

رابط **`NavigationDestination`** از {{domxref("Navigation API", "Navigation API", "", "nocode")}} مقصدی را که در پیمایش فعلی به آن پیمایش می‌شود، نمایش می‌دهد.

این رابط از طریق ویژگی {{domxref("NavigateEvent.destination")}} قابل دسترسی است.

{{InheritanceDiagram}}

## Instance properties

- {{domxref("NavigationDestination.id", "id")}} {{ReadOnlyInline}}
  - : اگر {{domxref("NavigateEvent.navigationType")}} برابر با `traverse` باشد، مقدار {{domxref("NavigationHistoryEntry.id", "id")}} مقصد {{domxref("NavigationHistoryEntry")}} را بازمی‌گرداند، در غیر این صورت یک رشتهٔ خالی.

- {{domxref("NavigationDestination.index", "index")}} {{ReadOnlyInline}}
  - : اگر {{domxref("NavigateEvent.navigationType")}} برابر با `traverse` باشد، مقدار {{domxref("NavigationHistoryEntry.index", "index")}} مقصد {{domxref("NavigationHistoryEntry")}} را بازمی‌گرداند، در غیر این صورت `-1`.

- {{domxref("NavigationDestination.key", "key")}} {{ReadOnlyInline}}
  - : اگر {{domxref("NavigateEvent.navigationType")}} برابر با `traverse` باشد، مقدار {{domxref("NavigationHistoryEntry.key", "key")}} مقصد {{domxref("NavigationHistoryEntry")}} را بازمی‌گرداند، در غیر این صورت یک رشتهٔ خالی.

- {{domxref("NavigationDestination.sameDocument", "sameDocument")}} {{ReadOnlyInline}}
  - : اگر ناوبری به همان `document` (سند) فعلی {{domxref("Document")}} باشد، `true` و در غیر این صورت `false` بازمی‌گرداند.

- {{domxref("NavigationDestination.url", "url")}} {{ReadOnlyInline}}
  - : نشانی اینترنتی (URL) که به آن ناوبری می‌شود را بازمی‌گرداند.

## Instance methods

- {{domxref("NavigationDestination.getState", "getState()")}}
  - : یک کپی از وضعیت موجود مرتبط با مقصد {{domxref("NavigationHistoryEntry")}} یا عملیات ناوبری (مثلاً {{domxref("Navigation.navigate()", "navigate()")}}) را به‌طور مناسب بازمی‌گرداند.

## Examples

```js
navigation.addEventListener("navigate", (event) => {
  // Exit early if this navigation shouldn't be intercepted,
  // e.g. if the navigation is cross-origin, or a download request
  if (shouldNotIntercept(event)) {
    return;
  }

  // Returns a URL() object constructed from the
  // NavigationDestination.url value
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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)
- [Navigation API live demo](https://mdn.github.io/dom-examples/navigation-api/) ([view demo source](https://github.com/mdn/dom-examples/tree/main/navigation-api))
```