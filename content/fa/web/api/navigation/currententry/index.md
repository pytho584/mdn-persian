---
title: "Navigation: currentEntry property"
short-title: currentEntry
slug: Web/API/Navigation/currentEntry
page-type: web-api-instance-property
browser-compat: api.Navigation.currentEntry
---

{{APIRef("Navigation API")}}

ویژگی فقط‑خواندنی **`currentEntry`** از رابط {{domxref("Navigation")}} یک شیء {{domxref("NavigationHistoryEntry")}} را برمی‌گرداند که مکان فعلی که کاربر در آن ناوبری شده است را نشان می‌دهد.

## Value

یک شیء {{domxref("NavigationHistoryEntry")}}.

## Examples

```js
function initHomeBtn() {
  // Get the key of the first loaded entry
  // so the user can always go back to this view.
  const { key } = navigation.currentEntry;
  backToHomeButton.onclick = () => {
    navigation.traverseTo(key);
  };
}
// Intercept navigate events, such as link clicks, and
// replace them with single-page navigations
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async handler() {
      // Navigate to a different view,
      // but the "home" button will always work.
    },
  });
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)