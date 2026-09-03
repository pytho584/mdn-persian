---
title: "NavigationTransition: finished property"
---

{{APIRef("Navigation API")}}

ویژگی فقط خواندنی **`finished`** از رابط {{domxref("NavigationTransition")}} یک {{jsxref("Promise")}} برمی‌گرداند که همزمان با فعال شدن رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} انجام می‌شود (resolve) یا همزمان با فعال شدن رویداد {{domxref("Navigation/navigateerror_event", "navigateerror")}} رد می‌شود (reject).

## Value

یک {{jsxref("Promise")}} که به `undefined` resolve می‌شود.

## Examples

```js
async function cleanupNavigation() {
  await navigation.transition.finished;
  // Navigation has completed successfully
  // Cleanup any ongoing monitoring
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)